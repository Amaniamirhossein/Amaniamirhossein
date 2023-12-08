# بازی حکم

import random

# کارت ها
suits = ["♠", "♥", "♦", "♣"]
ranks = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"]

# یک دسته کارت ایجاد کنید
deck = []
for suit in suits:
    for rank in ranks:
        deck.append((suit, rank))

# کارت ها را بُر بزنید
random.shuffle(deck)

# کارت های بازیکن اول را توزیع کنید
player_1_cards = deck[:11]

# کارت های بازیکن دوم را توزیع کنید
player_2_cards = deck[11:]

# کارت وسط را بُر بزنید
deck[5], deck[6] = deck[6], deck[5]

# کارت وسط را روی میز قرار دهید
trump_card = deck[5]

# بازی را شروع کنید
while True:
    # بازیکن اول بازی کند
    player_1_play = player_1_cards.pop()

    # بازیکن دوم بازی کند
    player_2_play = player_2_cards.pop()

    # نتیجه را تعیین کنید
    if trump_card[1] == "A" and player_1_play[1] == "A":
        result = "مساوی"
    elif trump_card[1] == player_1_play[1]:
        result = "مساوی"
    elif trump_card[1] > player_1_play[1]:
        result = "برنده شد بازیکن 1"
    else:
        result = "برنده شد بازیکن 2"

    # نتیجه را چاپ کنید
    print(f"بازیکن 1: {player_1_play[1]} | بازیکن 2: {player_2_play[1]} | نتیجه: {result}")

    # اگر بازی تمام شده است، بازی را متوقف کنید
    if len(player_1_cards) == 0 or len(player_2_cards) == 0:
        break

# برنده را اعلام کنید
if len(player_1_cards) > 0:
    print("برنده شد بازیکن 1")
else:
    print("برنده شد بازیکن 2")
