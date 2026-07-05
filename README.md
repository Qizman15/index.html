# --- ВЕБ-СЕРВЕР ---
async def handle(request):
    return web.FileResponse('index.html')  # Бот будет отдавать твой файл index.html


async def start_web():
    app = web.Application()
    app.router.add_get('/', handle)
    runner = web.AppRunner(app)
    await runner.setup()

    # 8080 — стандартный порт для таких задач
    site = web.TCPSite(runner, '0.0.0.0', 8080)
    await site.start()
    print("🌐 Веб-сервер запущен на порту 8080")
