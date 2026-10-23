import heapq

def a_star(graph, heuristic, start, goal):
    # Priority queue entries: (f_cost, g_cost, node, path)
    pq = [(heuristic[start], 0, start, [start])]
    visited = set()

    while pq:
        f, g, node, path = heapq.heappop(pq)

        if node == goal:
            return path, g

        if node in visited:
            continue
        visited.add(node)

        for neighbor, cost in graph[node]:
            if neighbor not in visited:
                new_g = g + cost
                new_f = new_g + heuristic[neighbor]
                heapq.heappush(pq, (new_f, new_g, neighbor, path + [neighbor]))
    return None, float('inf')

if __name__ == "__main__":
    graph = {
        'S': [('A', 1), ('B', 4)],
        'A': [('B', 2), ('C', 5), ('D', 12)],
        'B': [('C', 2)],
        'C': [('D', 3)],
        'D': []
    }
    heuristic = {'S': 7, 'A': 6, 'B': 4, 'C': 2, 'D': 0}

    path, cost = a_star(graph, heuristic, 'S', 'D')
    print("A* Search from S to D:")
    if path:
        print("Path found:", " -> ".join(path))
        print("Total cost:", cost)
    else:
        print("No path found.")
