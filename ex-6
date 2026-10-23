def vacuum_cleaner(state, location):
    # state: status of rooms A and B; location: 'A' or 'B'
    cost = 0
    print(f"Initial State: {state}, Vacuum at Room {location}")
    print("-" * 50)

    while "Dirty" in state.values():
        if state[location] == "Dirty":
            print(f"Room {location} is Dirty -> Action: SUCK")
            state[location] = "Clean"
            cost += 1
        else:
            print(f"Room {location} is Clean -> Action: MOVE")
            location = "B" if location == "A" else "A"
            cost += 1
        print(f"   Current State: {state}, Vacuum at Room {location}")

    print("-" * 50)
    print(f"Goal reached: all rooms are clean. Total actions (cost) = {cost}")

if __name__ == "__main__":
    initial_state = {"A": "Dirty", "B": "Dirty"}
    vacuum_cleaner(initial_state, "A")
