# -crypto-signals-app-mn
from telegram import Update
from telegram.ext import Updater, CommandHandler, CallbackContext

TOKEN = "توکن رباتت رو اینجا بذار"

def start(update: Update, context: CallbackContext):
    update.message.reply_text(
        "سلام! 👋\n"
        "من ربات سیگنال‌دهی هستم.\n"
        "از دستور /signal استفاده کن."
    )

def signal(update: Update, context: CallbackContext):
    signal_text = (
        "📈 *سیگنال امروز:*\n"
        "🚀 لانگ: بیت‌کوین در 29,800 دلار\n"
        "📉 شورت: اتریوم در 1,950 دلار\n"
        "🎯 هدف: 3-5 درصد سود\n"
        "⚠️ ضریب پیشنهادی: x3"
    )
    update.message.reply_text(signal_text, parse_mode="Markdown")

def main():
    updater = Updater(TOKEN)
    dispatcher = updater.dispatcher
    dispatcher.add_handler(CommandHandler("start", start))
    dispatcher.add_handler(CommandHandler("signal", signal))
    print("ربات فعال شد.")
    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()
