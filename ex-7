from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    order = []

    visited.add(start)
    while queue:
        node = queue.popleft()
        order.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return order

if __name__ == "__main__":
    graph = {
        'A': ['B', 'C'],
        'B': ['D', 'E'],
        'C': ['F'],
        'D': [],
        'E': ['F'],
        'F': []
    }
    start_node = 'A'
    print(f"BFS Traversal starting from node {start_node}:")
    print(" -> ".join(bfs(graph, start_node)))
