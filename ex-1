import heapq

GOAL_STATE = [[1, 2, 3], [4, 5, 6], [7, 8, 0]]

def get_manhattan_distance(state):
    distance = 0
    for i in range(3):
        for j in range(3):
            val = state[i][j]
            if val != 0:
                target_x = (val - 1) // 3
                target_y = (val - 1) % 3
                distance += abs(i - target_x) + abs(j - target_y)
    return distance

def get_neighbors(state):
    neighbors = []
    for i in range(3):
        for j in range(3):
            if state[i][j] == 0:
                x, y = i, j
                break

    moves = [(-1, 0), (1, 0), (0, -1), (0, 1)]
    for dx, dy in moves:
        nx, ny = x + dx, y + dy
        if 0 <= nx < 3 and 0 <= ny < 3:
            new_state = [row[:] for row in state]
            new_state[x][y], new_state[nx][ny] = new_state[nx][ny], new_state[x][y]
            neighbors.append(new_state)
    return neighbors

def solve_8_puzzle(start_state):
    pq = []
    # (f_cost, g_cost, state, path)
    heapq.heappush(pq, (get_manhattan_distance(start_state), 0, start_state, [start_state]))
    visited = set()

    while pq:
        f, g, current, path = heapq.heappop(pq)

        if current == GOAL_STATE:
            return path

        state_tuple = tuple(tuple(row) for row in current)
        if state_tuple in visited:
            continue
        visited.add(state_tuple)

        for neighbor in get_neighbors(current):
            if tuple(tuple(row) for row in neighbor) not in visited:
                h = get_manhattan_distance(neighbor)
                heapq.heappush(pq, (g + 1 + h, g + 1, neighbor, path + [neighbor]))
    return None

if __name__ == "__main__":
    initial_state = [
        [1, 2, 3],
        [4, 0, 5],
        [7, 8, 6]
    ]
    solution = solve_8_puzzle(initial_state)
    if solution:
        print(f"Solution found in {len(solution) - 1} steps:")
        for step_num, step in enumerate(solution):
            print(f"Step {step_num}:")
            for row in step:
                print(row)
            print()
    else:
        print("No solution found.")
