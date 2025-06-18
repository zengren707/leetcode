class Node {
constructor(key, val) {
this.key = key;
this.val = val;
this.prev = this.next = null;
}
}

class LRUCache {
constructor(capacity) {
this.capacity = capacity;
this.map = new Map();
this.head = new Node(0, 0);
this.tail = new Node(0, 0);
this.head.next = this.tail;
this.tail.prev = this.head;
}

    get(key) {
        if (!this.map.has(key)) return -1;
        const node = this.map.get(key);
        this._remove(node);
        this._add(node);
        return node.val;
    }

    put(key, value) {
        if (this.map.has(key)) this._remove(this.map.get(key));
        const node = new Node(key, value);
        this._add(node);
        this.map.set(key, node);
        if (this.map.size > this.capacity) {
            const lru = this.head.next;
            this._remove(lru);
            this.map.delete(lru.key);
        }
    }

    _remove(node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    _add(node) {
        node.prev = this.tail.prev;
        node.next = this.tail;
        this.tail.prev.next = node;
        this.tail.prev = node;
    }

}
