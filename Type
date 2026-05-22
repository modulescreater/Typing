import asyncio
from .. import loader, utils

@loader.tds
class TypeMod(loader.Module):
    """Модуль для печатающегося текста"""
    strings = {"name": "Type"}

    def __init__(self):
        self.config = loader.ModuleConfig()

    @loader.command(ru_doc="<текст> — эффект печатающегося текста")
    async def type(self, message):
        """Эффект печатающегося текста"""
        args = utils.get_args_raw(message)
        if not args:
            await utils.answer(message, "Используй: .type <текст>")
            return
        
        await message.delete()
        msg = await message.reply("...")
        
        current_text = ""
        for char in args:
            current_text += char
            try:
                await msg.edit(f"<code>{current_text}▋</code>")
                await asyncio.sleep(0.05)
            except Exception:
                await asyncio.sleep(1)
        
        await msg.edit(f"<code>{current_text}</code>")
