import telebot

bot = telebot.TeleBot('1730800670:AAHYt9XQ3Gx2T3ALuU2rR3svX010spKesks')

button2 = telebot.types.ReplyKeyboardMarkup(True)
button3 = telebot.types.ReplyKeyboardMarkup(True)

button2.row("📖Рамазон Таквими")
button2.row("🤲Огиз очиш дуоси", "🤲Огиз епиш дуоси")
button2.row("🕋Таровех Тасбехи")



@bot.message_handler(commands=['start'])
def start_message(message):
        bot.reply_to(message, 'Ассалому алайкум Рахматуллохи ва барокатух бизнинг рамазон ботимизга хуш келибсиз {} '
                              'бу бот оркали 13-апрел 12-майгача сахарлик ва ифторлик вактларини юборади. '.format(message.from_user.first_name), reply_markup=button2)

@bot.message_handler(content_types=['text'])
def send_text(message):
  if message.text.lower() == '📖рамазон таквими':
      with open("1.jpg", "rb") as f:
         img = f.read()
      bot.send_photo(photo=img, chat_id=message.from_user.id)
      with open("2.jpg", "rb") as f:
          img = f.read()
      bot.send_photo(photo=img, chat_id=message.from_user.id)

  elif message.text.lower() == '🤲огиз епиш дуоси':
      bot.send_message(message.chat.id, '_Огиз епиш дуоси:_\n\n'
                                        '*Навайту ан асума совма шахри Рамазона минал фажри\n*'
                                        '*илал магриби холисан лиллахи таъала*'
                                        '*Аллох акбар\n\n*'
                                        '*_Холис Аллох Таоло учун тонгдан кун ботгунча Рамазон\n'
                                        'рузасини тутишни ният килдим Аллох буюкдир_*', parse_mode='MarkdownV2')

  elif message.text.lower() == '🤲огиз очиш дуоси':
      bot.send_message(message.chat.id, '_Огиз очиш дуоси:_\n\n'
                                        '*Аддохумма лака сумту ва бика аманту ва ъалайка\n'
                                        'таваккалту ва ъала ризкика афторту Фагфирлий йа\n '
                                        'гоффару ма коддамту ва ма аххорту Бирохматика йа\n '
                                        'архамар рохимийн Аллоху Акбар\n\n*'
                                         '*_Аллохим Сенга иймон келтириб сен учун руза тутдим\n'
                                        'Сенга таваккал килдим Сен берган ризк билан ифторлик\n'
                                        'килдим Эй гунохларни Кечиргувчи мархаматларнинг\n'
                                        'Мархаматлиси Уз рахматинг билан олдинги ва кейинги \n'
                                        'гунохларимни кечир Аллох буюкдир Омийн_*', parse_mode='MarkdownV2')

  elif message.text.lower() == '🕋таровех тасбехи':
      bot.send_message(message.chat.id, '_Таровех Тасбехи:_\n\n' 
                    "*Субхана зил мулки вал малакут Суьхана зил\n"
                                        " иззати вал ъазомати вал кудроти вал кибрийаи вал\n"
                                        " жабарут Субханал маликил хаййил лазий ла ямут\n"
                                        " Суббухун куддусур Роббуна ва роббул малаикати\n"
                                        " варрух Ла илаха иллаллоху настагвируллох\n"
                                        " нас'алукал жанната ва наъузу бика минан нар*",  parse_mode='MarkdownV2'  )



bot.polling(none_stop=True)
