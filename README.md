import telebot
import random
import time

bot = telebot.TeleBot("")

OWNER_ID = "@Earner570"

# ================= MEMORY =================
user_memory = {}

def remember(uid, text):
    if uid not in user_memory:
        user_memory[uid] = []
    user_memory[uid].append(text)
    if len(user_memory[uid]) > 5:
        user_memory[uid].pop(0)

# ================= BASIC REPLIES =================

greetings = ["hello bhai 👋","hi 😊","aur bhai kya haal","kya scene hai","hello boss 😎","haan bol"]

casual = ["hmm theek hai","acha acha","sahi hai","samajh gaya","haan ye sahi hai"]

helping = ["bata kya help chahiye","clear bol kya problem hai","detail me bata","samjha deta hoon"]

funny = ["😂 bhai tu bhi na","lol 😄","haha mast tha","ye kya bol diya tune 😂"]

attitude = ["seedha bol bhai","faltu baat mat kar","time waste mat kar","focus kar"]

daily_chat = ["kya kar raha hai","khana kha liya","aaj kya plan hai","free ho kya"]

motivation = ["consistent rehna padega 💪","focus karo","mehnat ka result milta hai"]

confused = ["samajh nahi aaya","fir se bol","clear bol"]

# ================= SMART REPLIES =================
# ================= BIG REPLY SYSTEM =================

smart_replies = []

def add_replies(lst, repeat=1):
    for _ in range(repeat):
        smart_replies.extend(lst)

# ================= NORMAL CHAT =================
normal_chat = [
"haan bhai kya chal raha hai","tu bata sab sahi hai na","acha ye bata kya scene hai",
"haan samajh gaya main","thoda clear bol bhai","kya bol raha hai tu 😄",
"haan ye sahi hai","acha idea hai ye","mast chal raha hai","tu sahi bol raha hai",
"haan bhai full support","samajhne layak bol","thoda simple bol","acha fir kya hua",
"bhai ye interesting hai","free hai kya tu","busy lag raha hai 😂",
"haan bhai chill kar","itna serious kyu hai","normal baat kar bhai",
"haan ye kaam ka hai","acha solution hai","bhai mast hai"
]

# ================= WORK CHAT =================
work_chat = [
"bhai koi work hai kya","kaam chahiye urgent","earning ka kuch batao",
"bhai work dedo","online kaam milega kya","daily earning chahiye",
"koi genuine work hai kya","task based work hai kya",
"payment kitna milega","details bhejo","payment proof hai kya",
"bhai legit hai kya","real earning hai kya","fake to nahi hai na",
"bhai mujhe kaam chahiye","main ready hoon kaam ke liye",
"earning start karni hai","kaam sikha do"
]

# ================= OFFER SIDE =================
offer_chat = [
"haan bhai work available hai","dm me aao detail deta hoon",
"simple work hai tension mat lo","daily earning possible hai",
"proof bhi mil jayega","step by step guide milega",
"easy task hai","new users ke liye best hai",
"join karo fir batata hoon","limited slots hai jaldi karo",
"genuine work hai","daily payment milta hai",
"easy earning hai","free join hai"
]

# ================= ATTITUDE =================
attitude = [
"bhai dimag use kar","seedha bol","faltu ghooma mat",
"samajh ke bol","bhai logic laga thoda",
"thoda serious ho ja","aisa mat bol bhai",
"bhai normal baat kar","focus kar thoda"
]

# ================= MOTIVATION =================
motivation = [
"consistent rehna padega 💪","focus karo bhai",
"mehnat ka result milta hai","daily improve karo",
"हार मत मानना","kaam karte reh"
]
extra_big_2 = [

# 🔹 NORMAL CHAT
"aur bhai kya update hai","kya chal raha aajkal","scene kya hai aaj",
"tu bata kya kar raha hai","sab sahi chal raha na","kya plan hai aaj",
"haan bhai bata","acha fir kya socha","kya chal raha dimag me",
"tu free hai kya abhi","haan bol kya kaam hai","kya new chal raha",

# 🔹 CASUAL TALK
"acha acha samajh gaya","haan ye sahi lag raha","mast idea hai bhai",
"acha fir next kya","haan bhai continue kar","acha ye bhi theek hai",
"haan bhai sorted lag raha","acha fir try karte hai","haan bhai perfect",
"acha ye kaafi interesting hai","haan bhai clear hai","acha ye bhi chal jayega",

# 🔹 WORK DEMAND STYLE
"bhai koi earning system bata","kaam chahiye bhai jaldi",
"online earning ka kuch hai kya","bhai daily income ka bata",
"koi genuine source hai kya","bhai part time kaam milega",
"ghar baithe earning possible hai kya","bhai real kaam chahiye",
"fake nahi hona chahiye bhai","bhai legit hona chahiye",

# 🔹 OFFER SIDE
"haan bhai kaam available hai","easy earning hai try kar",
"step follow karo earning hogi","daily income possible hai",
"proof bhi mil jayega bhai","simple system hai tension nahi",
"join karo fir sab samjhaunga","bhai genuine hai try kar lo",
"limited slots hai jaldi karo","fast earning system hai",

# 🔹 PAYMENT RELATED
"payment daily milta hai","instant payout hai",
"upi payment available hai","proof bhi dikha denge",
"withdrawal easy hai","minimum low hai",
"bhai payment tension free hai","direct transfer hota hai",

# 🔹 ATTITUDE LIGHT
"bhai seedha bol kya chahiye","itna confuse mat kar",
"faltu mat ghooma baat ko","simple bol samajh aayega",
"bhai logic laga thoda","over mat kar",
"serious ho ja thoda","bhai clear bol",

# 🔹 FUN / REACTION
"😂 bhai kya bol raha hai","lol ye kya scene hai",
"haha mast tha bhai","ye kya bol diya tune",
"😂 bhai tu bhi na","ye funny tha",
"bhai hasaa diya tune","😂 full comedy",

# 🔹 MOTIVATION
"bhai consistency zaruri hai","daily kaam karega to grow karega",
"focus rakho bhai","mehnat ka result milta hai",
"thoda patience rakh","kaam karta reh",
"bhai give up mat kar","improve karta reh",

# 🔹 RANDOM CHAT
"kya khaaya aaj","bhai free ho kya",
"busy lag raha hai","kya kar raha hai abhi",
"haan bhai chill kar","scene set hai",
"mast chal raha hai","tu tension mat le",
"bhai sab theek ho jayega","relax kar"
] * 20

# ADD
smart_replies += extra_big_2
# ================= ADD MASS =================
add_replies(normal_chat, 20)
add_replies(work_chat, 20)
add_replies(offer_chat, 20)
add_replies(attitude, 15)
add_replies(motivation, 15)

# ================= FINAL SHUFFLE =================
random.shuffle(smart_replies)
smart_replies = []

smart_replies += greetings
smart_replies += casual
smart_replies += helping
smart_replies += funny
smart_replies += attitude
smart_replies += daily_chat
smart_replies += motivation
smart_replies += confused

# ================= AI =================

def ai_reply(text):
    text = text.lower()

    if "hi" in text or "hello" in text:
        return random.choice(greetings)

    elif "kya haal" in text:
        return "main badhiya 😎 tu bata"

    elif "help" in text:
        return random.choice(helping)

    elif "earn" in text or "money" in text:
        return "earning ke liye DM karo 👉 @Earner570"

    else:
        return random.choice(smart_replies)

# ================= HUMAN FEEL =================

def typing(chat_id):
    bot.send_chat_action(chat_id, 'typing')

def delay():
    time.sleep(random.randint(1,2))

# ================= START =================

@bot.message_handler(commands=['start'])
def start(msg):
    bot.reply_to(msg,"Bot online 😎")

# ================= PROMOTION =================

PROMO_TEXT = """🚀 New Promotion Alert 🚀

📢 Channel Grow + Earn

🔥 Join now:
https://t.me/Activeearners01
https://t.me/earnershelper
https://t.me/referchat1
https://t.me/Earners01

💰 DM 👉 @Earner570
"""

# ================= AUTO =================

@bot.message_handler(func=lambda m: True)
def handle(msg):
    text = msg.text.lower()

    # earning trigger
    if any(w in text for w in ["earn","work","kaam"]):
        bot.reply_to(msg,PROMO_TEXT)
        return

    # normal reply
    typing(msg.chat.id)
    delay()

    bot.reply_to(msg, ai_reply(text))

print("Bot running 🔥")
bot.infinity_polling()
