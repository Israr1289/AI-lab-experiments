import itertools

def solve_cryptarithmetic(formula):
    # Split formula into words and operators
    parts = formula.replace('+', ' + ').replace('=', ' = ').split()
    words = [p for p in parts if p.isalpha()]
    result_word = words[-1]
    input_words = words[:-1]

    unique_chars = set(''.join(words))
    assert len(unique_chars) <= 10, "Too many unique letters!"

    chars = list(unique_chars)
    leading_chars = {w[0] for w in words}

    for perm in itertools.permutations(range(10), len(chars)):
        char_map = dict(zip(chars, perm))

        # Check leading letters for zero
        if any(char_map[char] == 0 for char in leading_chars):
            continue

        def word_to_num(word):
            return sum(char_map[char] * (10 ** idx) for idx, char in enumerate(reversed(word)))

        input_sum = sum(word_to_num(w) for w in input_words)
        result_num = word_to_num(result_word)

        if input_sum == result_num:
            return char_map

    return None

if __name__ == "__main__":
    puzzle = "SEND + MORE = MONEY"
    print(f"Solving puzzle: {puzzle}")
    mapping = solve_cryptarithmetic(puzzle)
    if mapping:
        print("Solution found (Letter -> Digit mapping):")
        for k, v in sorted(mapping.items()):
            print(f"  {k} = {v}")
    else:
        print("No solution found.")
