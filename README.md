# Код для рботы с мини апкой

```javascript
import "dotenv/config";
import { Bot, InlineKeyboard } from "grammy";

const bot = new Bot(process.env.TOKEN);

bot.on("message:web_app_data", (ctx) => {
    console.log("hi");
    console.log(ctx);
    const data = JSON.parse(ctx.webAppData.data);
    ctx.reply(`Your timezone offset in minutes: ${data.timezoneOffset}`);
});

bot.command("start", (ctx) => {
    const url = "https://fdw-tools.github.io/timezone-getter/"
    const keyboard = new InlineKeyboard().webApp("Set Timezone", url); 

    ctx.reply("Hi", {
        reply_markup: keyboard,
    }); 
});
```


bot.start();
