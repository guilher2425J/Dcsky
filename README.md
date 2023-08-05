import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.members = True

bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    print(f'Bot está pronto como {bot.user.name}')

@bot.event
async def on_member_join(member):
    channel = member.guild.system_channel

    if channel is not None:
        # Enviar mensagem de boas-vindas no canal do servidor
        mensagem = f'Bem-vindo ao servidor, {member.mention}!'
        await channel.send(mensagem)

        # Definir o banner personalizado (replace 'URL_DO_BANNER' com a URL da imagem)
        await member.guild.edit(banner=None)  # Limpa o banner atual
        await member.guild.edit(banner='https://www.canva.com/design/DAFqtXESqqg/4sj8_7fQBZfE_jb221hBlQ/edit?utm_content=DAFqtXESqqg&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton')

        # Enviar mensagem privada para o usuário
        mensagem_privada = f'Olá, {member.name}! Bem-vindo ao nosso servidor. Esperamos que você tenha uma ótima experiência aqui!'
        await member.send(mensagem_privada)

bot.run('MTA1NTA5MjY5MDM2ODMzNTkxMw.GK_OTQ.ecsiI5iJsPs4dahaqJvGrL15H4LYsRE9Z5CH88')
