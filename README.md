import random

def monty_hall(num_trials=1000):
    """Simulates the Monty Hall problem and returns the win percentages."""
    stay_wins = 0
    switch_wins = 0

    for _ in range(num_trials):
        # Randomly assign the car to a door
        winning_door = random.randint(0, 2)

        # Player makes an initial choice
        player_choice = random.randint(0, 2)

        # Monty opens a door that is not the winning door and not the player's choice
        monty_options = [i for i in range(3) if i != winning_door and i != player_choice]
        monty_opens = random.choice(monty_options)

        # Strategy 1: Stay with the initial choice
        if player_choice == winning_door:
            stay_wins += 1

        # Strategy 2: Switch to the remaining door
        switch_choice = [i for i in range(3) if i != player_choice and i != monty_opens][0]
        if switch_choice == winning_door:
            switch_wins += 1

    stay_win_percentage = (stay_wins / num_trials) * 100
    switch_win_percentage = (switch_wins / num_trials) * 100

    return stay_win_percentage, switch_win_percentage

# Run the simulation
stay_win_percentage, switch_win_percentage = monty_hall()

print(f"Staying with the initial choice wins {stay_win_percentage:.2f}% of the time.")
print(f"Switching doors wins {switch_win_percentage:.2f}% of the time.")
