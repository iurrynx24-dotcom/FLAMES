import time
import sys

# Typing Animation
def type_text(text, speed=0.04):
    for char in text:
        sys.stdout.write(char)
        sys.stdout.flush()
        time.sleep(speed)
    print()

# Loading Animation
def loading():
    type_text("\n💖 Calculating your FLAMES result", 0.03)
    for _ in range(5):
        sys.stdout.write(".")
        sys.stdout.flush()
        time.sleep(0.5)
    print("\n")

def flames(name1, name2):
    n1 = list(name1.replace(" ", "").lower())
    n2 = list(name2.replace(" ", "").lower())

    type_text("\n=== STEP 1: Splitting Names ===", 0.03)
    type_text(f"Name 1: {n1}")
    type_text(f"Name 2: {n2}")

    # Remove common letters
    for letter in n1[:]:
        if letter in n2:
            n1.remove(letter)
            n2.remove(letter)

    type_text("\n=== STEP 2: Removing Common Letters ===", 0.03)
    type_text(f"Remaining Name 1: {n1}")
    type_text(f"Remaining Name 2: {n2}")

    count = len(n1) + len(n2)
    type_text(f"\nRemaining Letter Count: {count}")

    flames = ["F", "L", "A", "M", "E", "S"]
    meaning = {
        "F": "👫 Friends",
        "L": "❤️ Lovers",
        "A": "💖 Affection",
        "M": "💍 Marriage",
        "E": "💢 Enemies",
        "S": "🤝 Siblings"
    }

    type_text("\n=== STEP 3: FLAMES Elimination ===", 0.03)

    index = 0
    while len(flames) > 1:
        index = (index + count - 1) % len(flames)
        removed = flames.pop(index)
        type_text(f"❌ Removed: {removed}  →  {flames}", 0.02)
        time.sleep(0.4)

    loading()

    type_text("  FINAL RESULT", 0.06)
    type_text(f"{name1} ❤️ {name2}", 0.05)
    type_text(f"Result: {meaning[flames[0]]}", 0.07)


# =====================================
#            MAIN
# =====================================

type_text("=" * 40)
type_text("           F L A M E S ", 0.05)
type_text("      Filipino Love Calculator", 0.03)
type_text(" will he/she become yours?? lets see...", 0.10)
type_text("=" * 40)

name1 = input("\n♂️  Enter His Name : ")
name2 = input("♀️ Enter Her Name: ")

loading()
flames(name1, name2)

type_text("\n Thanks for playing FLAMES!", 0.04)
type_text("\n Did you get him/her or not?" , 0.10)
