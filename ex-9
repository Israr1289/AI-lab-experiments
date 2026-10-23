import itertools

def travelling_salesman(dist, cities):
    start = cities[0]
    others = cities[1:]
    best_cost = float('inf')
    best_path = None

    for perm in itertools.permutations(others):
        path = [start] + list(perm) + [start]
        cost = 0
        for i in range(len(path) - 1):
            cost += dist[path[i]][path[i + 1]]
        print(f"Route: {' -> '.join(path)} | Cost: {cost}")
        if cost < best_cost:
            best_cost = cost
            best_path = path
    return best_path, best_cost

if __name__ == "__main__":
    cities = ['A', 'B', 'C', 'D']
    dist = {
        'A': {'A': 0,  'B': 10, 'C': 15, 'D': 20},
        'B': {'A': 10, 'B': 0,  'C': 35, 'D': 25},
        'C': {'A': 15, 'B': 35, 'C': 0,  'D': 30},
        'D': {'A': 20, 'B': 25, 'C': 30, 'D': 0}
    }
    print("Travelling Salesman Problem (Brute Force):")
    path, cost = travelling_salesman(dist, cities)
    print("\nShortest Route:", " -> ".join(path))
    print("Minimum Cost:", cost)
