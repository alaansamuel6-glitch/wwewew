import telebot
import os
import random
import requests

bot = telebot.TeleBot("dsadsa")
images = "mem1,mem2,mem3"
quotes = [
    "Продукты питания	разлагаются 7-14 дней»",
    "Влажные салфеткиразлагаются более 100 лет",
    "Батарейки и аккумуляторы до 100 лет",
    "Жестяные банки до 90 лет",
    "Пластиковые бутылки от 450 до 1000+ лет",
    "Стекло более 1 000 000 лет (практически не разлагается)",
    "Офисная бумага до 2 лет",
    "Хлопковая одежда	2-5 месяцев",
]

@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "Привет! Я бот, я бот который умеет рассказывать рандомные факты  о размножение отходов пиши чтобы узнать : /quote, что бы узнать что выкидывать в какую мусорку пиши /bumaga /plastic /steklo")


@bot.message_handler(commands=['quote'])
def send_quote(message):
    quote = random.choice(quotes)
    bot.reply_to(message, quote)

@bot.message_handler(commands=['plastic'])
def send_mem(message):
    with open('images/mem1.png', 'rb') as f:  
        bot.send_photo(message.chat.id, f)

@bot.message_handler(commands=['bumaga'])
def send_mem(message):
    with open('images/mem3.png', 'rb') as f:  
        bot.send_photo(message.chat.id, f)
        
@bot.message_handler(commands=['steklo'])
def send_mem(message):
    with open('images/mem2.png', 'rb') as f:  
        bot.send_photo(message.chat.id, f)

@bot.message_handler(func=lambda message: True)
def echo_all(message):
    bot.reply_to(message, message.text)

bot.polling()
