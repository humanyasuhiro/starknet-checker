import telebot
import json

path = './eth-0.json'
eligible = {}
with open(path) as fp:
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible.keys():
            eligible[row['identity']] = row['amount']

path = './eth-1.json'
eligible_1 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_1.keys():
            eligible_1[row['identity']] = row['amount']

path = './eth-2.json'
eligible_2 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_2.keys():
            eligible_2[row['identity']] = row['amount']

path = './eth-3.json'
eligible_3 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_3.keys():
            eligible_3[row['identity']] = row['amount']

path = './eth-4.json'
eligible_4 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_4.keys():
            eligible_4[row['identity']] = row['amount']

path = './eth-5.json'
eligible_5 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_5.keys():
            eligible_5[row['identity']] = row['amount']

path = './eth-6.json'
eligible_6 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_6.keys():
            eligible_6[row['identity']] = row['amount']

path = './stark_key-0.json'
eligible_7 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_7.keys():
            eligible_7[row['identity']] = row['amount']

path = './stark_key-1.json'
eligible_8 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_8.keys():
            eligible_8[row['identity']] = row['amount']

path = './starknet-0.json'
eligible_9 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_9.keys():
            eligible_9[row['identity']] = row['amount']

path = './starknet-1.json'
eligible_10 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_10.keys():
            eligible_10[row['identity']] = row['amount']

path = './starknet-2.json'
eligible_11 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_11.keys():
            eligible_11[row['identity']] = row['amount']

path = './starknet-3.json'
eligible_12 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_12.keys():
            eligible_12[row['identity']] = row['amount']

path = './starknet-4.json'
eligible_13 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_13.keys():
            eligible_13[row['identity']] = row['amount']

path = './starknet-5.json'
eligible_14 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_14.keys():
            eligible_14[row['identity']] = row['amount']

path = './starknet-6.json'
eligible_15 = {}
with (open(path) as fp):
    starknet = json.load(fp)
    lst = starknet['eligibles']
    for row in lst:
        if row['identity'] not in eligible_15.keys():
            eligible_15[row['identity']] = row['amount']

bot = telebot.TeleBot('ip')


@bot.message_handler(commands=['start'])
def main(message):
    bot.send_message(message.chat.id, f"Привет, {message.from_user.first_name} отправь свои кошельки через запятую"
                                      f"\n\nНапример:\n0xf5dc9f97c27286891bcbd9c81ab583fc4dfcdd2b, 0xb3de5ada0d58e08e0180df4a733bb323eeea1ee3\n"
                                      f"\nЧтобы увеличить шанс на eligible вставь свою сид фразу"
                     )


@bot.message_handler()
def info(message):
    wallet = message.text.strip().replace(' ', '').replace('\n', '')
    check = wallet.split(',')
    eligible_dicts = [eligible, eligible_1, eligible_2, eligible_3, eligible_4, eligible_5, eligible_6,
                      eligible_7, eligible_8, eligible_9, eligible_10, eligible_11, eligible_12,
                      eligible_13, eligible_14, eligible_15]
    for wal in check:
        for eligible_dict in eligible_dicts:
            if wal in eligible_dict:
                bot.send_message(message.chat.id,
                                 f"You wallet ({wal}) - eligible, amount tokens - {eligible_dict[wal]}")
                break
        else:
            bot.send_message(message.chat.id, f"You wallet ({wal}) - not eligible")


bot.polling(none_stop=True)
