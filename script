import requests
import telebot
from telebot.types import Message
from telebot import types
from telebot.types import User
import pickle
import json

bot = telebot.TeleBot("865000205:AAFasfTnPeXgOXwYQIOq1HdmcIpQf4IGKFQ")

smiler = [
    "🌤",
    "☀"
    "⛅",
    "❄"
]

@bot.message_handler(commands=['start'])
def send_welcome(message):
	bot.reply_to(message, "Привет! \nДавай узнаем погоду на сегодня?\n\nНапиши свой город (на английском языке)" + smiler[0])

@bot.message_handler(content_types=['text'])
def sendWeather(message:Message):
    w_url = "http://api.openweathermap.org/data/2.5/weather?q={},ru&APPID=1e3bf8aff7994eca0176c467a12f7ce2&units=metric".format(message.text)
    r = requests.get(w_url)
    data = r.json()
    temp = data["main"]['temp']
    name = data['name']
    answer = "Температура воздуха в городе {} = {} °C".format(name, temp)

    bot.reply_to(message, answer)


bot.polling()
