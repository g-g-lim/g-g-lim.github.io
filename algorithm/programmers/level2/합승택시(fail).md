---
layout: page
title: "/합승택시(fail)"
permalink: /합승택시(fail)
---

# 합승택시(fail)

<img src="/assets/images/programmers/합승택시(fail).png" width="100%" alt="합승택시(fail)" />
<img src="/assets/images/programmers/합승택시(fail)-1.png" width="100%" alt="합승택시(fail)" />


```javascript
class MinHeap {
    constructor() {
        this.heap = [];
    }

    // 힙에 요소 추가
    push(element) {
        this.heap.push(element);
        this.bubbleUp();
    }

    // 최소값 제거 및 반환
    pop() {
        if (this.isEmpty()) return null;

        const min = this.heap[0];
        const last = this.heap.pop();

        if (this.heap.length > 0) {
            this.heap[0] = last;
            this.bubbleDown();
        }

        return min;
    }

    // 최소값 확인 (제거하지 않음)
    peek() {
        return this.isEmpty() ? null : this.heap[0];
    }

    // 힙이 비어있는지 확인
    isEmpty() {
        return this.heap.length === 0;
    }

    // 힙의 크기 반환
    size() {
        return this.heap.length;
    }

    // 위로 거품 올리기 (새로 추가된 요소를 적절한 위치로)
    bubbleUp() {
        let index = this.heap.length - 1;

        while (index > 0) {
            const parentIndex = Math.floor((index - 1) / 2);

            if (this.heap[parentIndex][1] <= this.heap[index][1]) {
                break;
            }

            // 부모와 자식 교환
            [this.heap[parentIndex], this.heap[index]] = [this.heap[index], this.heap[parentIndex]];
            index = parentIndex;
        }
    }

    // 아래로 거품 내리기 (루트를 적절한 위치로)
    bubbleDown() {
        let index = 0;

        while (true) {
            let smallest = index;
            const leftChild = 2 * index + 1;
            const rightChild = 2 * index + 2;

            // 왼쪽 자식이 더 작은지 확인
            if (leftChild < this.heap.length &&
                this.heap[leftChild][1] < this.heap[smallest][1]) {
                smallest = leftChild;
            }

            // 오른쪽 자식이 더 작은지 확인
            if (rightChild < this.heap.length &&
                this.heap[rightChild][1] < this.heap[smallest][1]) {
                smallest = rightChild;
            }

            // 더 작은 자식이 없다면 종료
            if (smallest === index) {
                break;
            }

            // 부모와 자식 교환
            [this.heap[index], this.heap[smallest]] = [this.heap[smallest], this.heap[index]];
            index = smallest;
        }
    }
}

function dijkstra(n, s, graph, target) {
    const visited = Array(n).fill(Infinity)
    visited[s - 1] = 0;
    const queue = new MinHeap();
    queue.push([s, 0]);

    while (queue.size() > 0) {
        const [from, sum] = queue.pop();

        if (target !== undefined && +from === target) {
            return { targetDistance: sum, visited }
        }

        for (const [to, weight] of Object.entries(graph[from])) {
            if (visited[to - 1] >= sum + weight) {
                visited[to - 1] = sum + weight;
                queue.push([to, visited[to - 1]]);
            }
        }
    }

    return { targetDistance: undefined, visited }
}

function solution(n, s, a, b, fares) {
    const graph = {};
    for (const f of fares) {
        const [from, to, price] = f;
        if (graph[from] === undefined) {
            graph[from] = { [to]: price };
        } else {
            graph[from][to] = price;
        }
        if (graph[to] === undefined) {
            graph[to] = { [from]: price };
        } else {
            graph[to][from] = price;
        }
    }

    const { visited } = dijkstra(n, s, graph);
    let min = visited[a - 1] + visited[b - 1];

    for (let i = 0; i < visited.length; i++) {
        let v = visited[i];
        if (v === Infinity || v === 0) {
            continue;
        }
        if (a - 1 === i) {
            const bd = dijkstra(n, i + 1, graph, b);
            min = Math.min(min, v + bd.targetDistance)
        } else if (b - 1 === i) {
            const ad = dijkstra(n, i + 1, graph, a);
            min = Math.min(min, v + ad.targetDistance)
        } else {
            const ad = dijkstra(n, i + 1, graph, a);
            const bd = dijkstra(n, i + 1, graph, b);
            min = Math.min(min, v + ad.targetDistance + bd.targetDistance)
        }
    }

    return min;
}
```