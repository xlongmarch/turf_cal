def get_winning_odds(count):
    odds = []
    for i in range(count):
        while True:
            try:
                odd = float(input(f"Enter winning odd {i + 1}: "))
                odds.append(odd)
                break
            except ValueError:
                print("Invalid input. Please enter a valid number.")
    return odds

def calculate_double_bet_payout(odds, investment):
    payouts = []
    for i in range(len(odds)):
        for j in range(i + 1, len(odds)):
            payout = investment * odds[i] * odds[j]
            payouts.append((odds[i], odds[j], payout))
    return payouts

def main():
    while True:
        try:
            count = int(input("Enter the number of winning odds: "))
            if count > 0:
                break
            else:
                print("The number of winning odds must be greater than 0.")
        except ValueError:
            print("Invalid input. Please enter a valid number.")

    odds = get_winning_odds(count)

    while True:
        try:
            investment = float(input("Enter the amount to invest in each double: "))
            break
        except ValueError:
            print("Invalid input. Please enter a valid number.")

    payouts = calculate_double_bet_payout(odds, investment)

    print("\nCalculated Payouts:")
    for i, (odd1, odd2, payout) in enumerate(payouts, 1):
        print(f"Double Bet {i}: {odd1} * {odd2} * {investment} = ${payout:.2f}")

if __name__ == "__main__":
    main()
