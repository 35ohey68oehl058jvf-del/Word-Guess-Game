import random

# قائمة الكلمات
words = ["random", "anas", "goker", "coin", "python", "developer"]

# اختيار كلمة عشوائية
random_word = random.choice(words)

# تحويل الكلمة إلى قائمة حروف
letters = list(random_word)

# عرض عدد الحروف للمستخدم
print("🔤 Welcome to the Word Guess Game!")
print(f"The word has {len(random_word)} letters.")
print("_ " * len(random_word))

# إنشاء مجموعة لتخزين الحروف الصحيحة
correct_guesses = set()
attempts = 6  # عدد المحاولات

while attempts > 0:
    guessed = input("\nGuess a letter: ").lower()

    if guessed in letters:
        correct_guesses.add(guessed)
        print("✅ Correct!")
    else:
        attempts -= 1
        print(f"❌ Wrong! Attempts left: {attempts}")

    # عرض الحروف اللي المستخدم اكتشفها
    display = [letter if letter in correct_guesses else "_" for letter in random_word]
    print(" ".join(display))

    # التحقق من الفوز
    if set(letters) == correct_guesses:
        print("\n🎉 You guessed the word! It was:", random_word)
        break
else:
    print("\n💀 Game over! The word was:", random_word)
