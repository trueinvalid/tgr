import random
from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import Application, CommandHandler, CallbackQueryHandler, MessageHandler, filters

token = "7429008005:AAGdQD6-J_AYc8WQsWqiXB4g9rzmov4VsZI"
async def start(update: Update, context):
    await update.message.reply_text("Привет!")
    buttons = [
        [InlineKeyboardButton("Анекдот",callback_data="joke")],
        [InlineKeyboardButton("Факт о Python", callback_data="fact")],
        [InlineKeyboardButton("Музыка", callback_data="music")],
        [InlineKeyboardButton("Фото", callback_data="photo")],
    ]
    keyboard = InlineKeyboardMarkup(buttons)
    await update.message.reply_text("Выберите действие", reply_markup=keyboard)

async def button_click(update: Update, context):
    query = update.callback_query
    await query.answer()
    if query.data == "joke":
        await query.message.reply_text("Употребляй зло, но не злоупотребляй!")
    elif query.data == "fact":
        await query.message.reply_text("Python был назван не в честь змеи, а в честь названия цирка")
    elif query.data == "music":
        await query.message.reply_text("Все топовые треки: ")
        myMusic = ["ridonezz_sia-feat-sean-paul-cheap-thrills.mp3", "88Rising - Best Lover (feat. Bibi).mp3", "Brent_Morgan_-Gonna_Be_Okay(musmore.com).mp3", "Burak Yeter ft. Gerson Rafael - See You Again.mp3"]
        for music in myMusic:
            with open(music,"rb") as audio:
                await query.message.reply_audio(audio)
    elif query.data == "photo":
        await query.message.reply_text("Рандомные фотки:")
        myPhoto = ["https://gb.ru/blog/wp-content/uploads/2022/11/01-3.jpg.webp", "myPhoto.jpg"]
        await query.message.reply_photo(random.choice(myPhoto))



app = Application.builder().token(token).build() # создание бота
app.add_handler(CommandHandler("start",start))
app.add_handler(CallbackQueryHandler(button_click))

app.run_polling() # запуск телеграм бота
