from collections import deque

def is_valid(m, c):
    if m < 0 or c < 0 or m > 3 or c > 3:
        return False
    if m > 0 and m < c:
        return False
    if (3 - m) > 0 and (3 - m) < (3 - c):
        return False
    return True

def missionaries_cannibals_bfs():
    # State: (M_left, C_left, Boat_position), Path
    initial_state = (3, 3, 1)
    goal_state = (0, 0, 0)

    queue = deque([(initial_state, [initial_state])])
    visited = set([initial_state])

    # Possible boat moves (M, C)
    moves = [(1, 0), (2, 0), (0, 1), (0, 2), (1, 1)]

    while queue:
        current, path = queue.popleft()
        m, c, boat = current

        if current == goal_state:
            return path

        multiplier = -1 if boat == 1 else 1

        for dm, dc in moves:
            new_m = m + multiplier * dm
            new_c = c + multiplier * dc
            new_boat = 1 - boat

            if is_valid(new_m, new_c):
                new_state = (new_m, new_c, new_boat)
                if new_state not in visited:
                    visited.add(new_state)
                    queue.append((new_state, path + [new_state]))

    return None

if __name__ == "__main__":
    print("Solving Missionaries and Cannibals Problem:")
    solution = missionaries_cannibals_bfs()
    if solution:
        for step, state in enumerate(solution):
            boat_side = "Left" if state[2] == 1 else "Right"
            print(f"Step {step}: Left Bank -> M:{state[0]}, C:{state[1]} | Boat is on {boat_side} bank")
    else:
        print("No solution found.")
