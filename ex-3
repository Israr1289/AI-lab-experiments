from collections import deque

def water_jug_bfs(jug1_cap, jug2_cap, target):
    visited = set()
    queue = deque()

    # Queue stores (jug1, jug2, path)
    queue.append((0, 0, [(0, 0)]))
    visited.add((0, 0))

    while queue:
        x, y, path = queue.popleft()

        if x == target or y == target:
            return path

        # Possible rules/transitions
        transitions = [
            (jug1_cap, y),  # Fill Jug 1
            (x, jug2_cap),  # Fill Jug 2
            (0, y),         # Empty Jug 1
            (x, 0),         # Empty Jug 2
            # Pour Jug 1 -> Jug 2
            (x - min(x, jug2_cap - y), y + min(x, jug2_cap - y)),
            # Pour Jug 2 -> Jug 1
            (x + min(y, jug1_cap - x), y - min(y, jug1_cap - x))
        ]

        for state in transitions:
            if state not in visited:
                visited.add(state)
                queue.append((state[0], state[1], path + [state]))

    return None

if __name__ == "__main__":
    jug1 = 4
    jug2 = 3
    target = 2
    print(f"Solving Water Jug Problem (Capacities: {jug1}L, {jug2}L, Target: {target}L):")
    solution = water_jug_bfs(jug1, jug2, target)
    if solution:
        for step, state in enumerate(solution):
            print(f"Step {step}: Jug 1 = {state[0]}L, Jug 2 = {state[1]}L")
    else:
        print("No solution found.")
