Телеграмм бот на Ruby.

loop do
  begin
    Telegram::Bot::Client.run(TOKEN) do |bot|
      bot.listen do |message|
        Thread.start(message) do |message|
          begin
            case message.text
            when '/start', 'Привет', 'привет', 'qq', 'ку'
              kb = 
              [
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Ссылки'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Вопросы')
                ],
                Telegram::Bot::Types::KeyboardButton.new(text: 'Поддержать')
              ]

              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: text, reply_markup: markup, parse_mode: "Markdown")
            end
            
            case message.text
            when 'Ссылки'
              kb = 
              [
                [
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Мой VK', url: 'https://vk.com/alfedovgroup')
                ],
                [
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Twitch', url: 'https://www.twitch.tv/alfedov'),
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'YouTube', url: 'https://www.youtube.com/c/AlfedovLUL'),
                ],
                [
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Discord', url: 'https://discord.com/invite/5NUDe6w'),
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Группа VK', url: 'https://vk.com/alfedovgroup')
                ]
              ]
              
              markup = Telegram::Bot::Types::InlineKeyboardMarkup.new(inline_keyboard: kb)
              bot.api.send_message(chat_id: message.from.id, text: 'Эти ссылки помогут тебе быть в курсе всех событий.', reply_markup: markup)
              
            when 'Вопросы'
              kb = 
              [
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Как тебя зовут?'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Сколько тебе лет?'),
                ],
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Когда стрим?'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Когда видос?'),
                ],
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Как попасть на МШ?'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Какой приватный сервер посоветуешь?'),
                ],
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Какой у тебя комп?'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'В каком городе живёшь?'),
                ],
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Как придумал свой ник?'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'В какой программе монтируешь?'),
                ],
                  Telegram::Bot::Types::KeyboardButton.new(text: '<< Назад')
              ]
              
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: 'Выбери интересующий тебя вопрос.', reply_markup: markup)

            when 'Поддержать'
              kb = 
              [
                Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Donation', url: 'https://google.com')
              ]

              markup = Telegram::Bot::Types::InlineKeyboardMarkup.new(inline_keyboard: kb)
              bot.api.send_message(chat_id: message.from.id, text: donat, reply_markup: markup, parse_mode: "Markdown")
            end

            case message.text
            when 'Как тебя зовут?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer1 , reply_markup: markup, parse_mode: "Markdown")
            when 'Сколько тебе лет?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer2 , reply_markup: markup, parse_mode: "Markdown")
            when 'Когда стрим?'
              kb = 
              [
                [
                  Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Discord', url: 'https://discord.com/invite/5NUDe6w')
                ],
                Telegram::Bot::Types::InlineKeyboardButton.new(text: 'Telegram', url: 'https://t.me/alfedovgroup')
              ]

              markup = Telegram::Bot::Types::InlineKeyboardMarkup.new(inline_keyboard: kb)
              bot.api.send_message(chat_id: message.from.id, text: answer3 , reply_markup: markup, parse_mode: "Markdown")
            when 'Когда видос?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer4 , reply_markup: markup, parse_mode: "Markdown")
            when 'Как попасть на МШ?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer5 , reply_markup: markup, parse_mode: "Markdown")
            when 'Какой приватный сервер посоветуешь?'
              kb =
              [
                Telegram::Bot::Types::InlineKeyboardButton.new(text: 'SubShield', url: 'https://buy.shield.land/Alfedov')
              ]

              markup = Telegram::Bot::Types::InlineKeyboardMarkup.new(inline_keyboard: kb)
              bot.api.send_message(chat_id: message.from.id, text: answer6 , reply_markup: markup, parse_mode: "Markdown")
            when 'Какой у тебя комп?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer7 , reply_markup: markup, parse_mode: "Markdown")
            when 'В каком городе живёшь?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer8 , reply_markup: markup, parse_mode: "Markdown")
            when 'Как придумал свой ник?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer9 , reply_markup: markup, parse_mode: "Markdown")
            when 'В какой программе монтируешь?'
              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: answer10 , reply_markup: markup, parse_mode: "Markdown")
            end

            case message.text
            when '<< Назад'
              kb = 
              [
                [
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Ссылки'),
                  Telegram::Bot::Types::KeyboardButton.new(text: 'Вопросы')
                ],
                Telegram::Bot::Types::KeyboardButton.new(text: 'Поддержать')
              ]

              markup = Telegram::Bot::Types::ReplyKeyboardMarkup.new(keyboard: kb)
              bot.api.send_message(chat_id: message.chat.id, text: 'Выбери что тебя интересует.', reply_markup: markup)
            end
          rescue
          end
        end
      end
    end
  rescue
  end
end
