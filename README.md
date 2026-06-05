import tkinter as tk

fase = 1

def clicou(opcao):
    global fase
    
    if fase == 1:
        if opcao == "sim":
            lbl_texto.config(text="Excelente escolha! Começaremos nossa jornada histórica hoje!\n\nVAMOS, AJUDE-ME A ESPALHAR AS 95 TESES!\n\n(Clique em qualquer botão para continuar)")
            fase = 2
        else:
            lbl_texto.config(text="Você decidiu continuar fiel à Igreja tradicional. Fim do jogo.\n\nFeche a janela para sair.")
            btn_sim.pack_forget() 
            btn_nao.pack_forget()
            lbl_divisor.pack_forget()

    elif fase == 2:
        lbl_texto.config(text="Sabe qual é a nova invenção que vai nos ajudar a espalhar essas ideias rapidamente?")
        fase = 3

    elif fase == 3:
        if opcao == "sim":
            texto = "Ótimo! Então você já sabe que a prensa de tipos móveis vai revolucionar o conhecimento.\n\n"
        else:
            texto = "Estás vendo isto? É a PRENSA DE GUTENBERG!\nA maior tecnologia do momento, serve para imprimir livros em massa e traduzir a Bíblia!\n\n"
        
        texto += "O TEMPO PASSOU...\n\nDe repente, o Papa descobre as críticas e envia uma ordem de retratação: 'EXCOMUNHÃO À VISTA!' 📜\nDevemos queimar o documento papal em praça pública?"
        lbl_texto.config(text=texto)
        fase = 4

    elif fase == 4:
        if opcao == "sim":
            lbl_texto.config(text="Bela atitude de coragem! O movimento ganha força entre os príncipes alemães.\n\nNasce a REFORMA PROTESTANTE! ⛪\nParabéns! Você ajudou a mudar a história da Europa!\n\nDeseja jogar novamente?")
        else:
            lbl_texto.config(text="Oh não! Você recuou com medo da fogueira. Sem o seu apoio, o movimento enfraqueceu na região...\n\nVocê acabou virando um camponês comum. Que sufoco! 😰\n\nDeseja jogar novamente?")
        fase = 5

    elif fase == 5:
        if opcao == "sim":
            fase = 1
            lbl_texto.config(text="Olá meu jovem.. sou Martinho Lutero, um monge alemão.\nQueres me apoiar contra a venda de indulgências?")
        else:
            lbl_texto.config(text="Obrigado por revisar a história, estudante! Até a próxima! ⛪")
            btn_sim.pack_forget()
            btn_nao.pack_forget()
            lbl_divisor.pack_forget()

janela = tk.Tk()
janela.title("A Reforma Protestante - 7º Ano")
janela.geometry("460x340")
janela.configure(bg="#ffffff", highlightbackground="#e0e0e0", highlightthickness=1) 

lbl_texto = tk.Label(
    janela, 
    text="Olá meu jovem.. sou Martinho Lutero, um monge alemão.\nQueres me apoiar contra a venda de indulgências?", 
    font=("Arial", 11),
    bg="#ffffff",       
    fg="#34495e",       
    wraplength=400,
    justify="center"
)
lbl_texto.pack(pady=35, expand=True)

lbl_divisor = tk.Label(
    janela,
    text="·  ·  ·  ·  ·  📜  ·  ·  ·  ·  ·",
    font=("Arial", 10),
    bg="#ffffff",
    fg="#bdc3c7"
)
lbl_divisor.pack(pady=5)

estilo_botao = {
    "font": ("Arial", 9, "bold"),
    "bg": "#ffffff",         
    "fg": "#555555",         
    "activebackground": "#eaeaea", 
    "relief": "groove",      
    "bd": 1,                  
    "width": 12,
    "height": 1
}

btn_sim = tk.Button(janela, text="SIM", **estilo_botao, command=lambda: clicou("sim"))
btn_sim.pack(side="left", padx=55, pady=25)

btn_nao = tk.Button(janela, text="NÃO", **estilo_botao, command=lambda: clicou("nao"))
btn_nao.pack(side="right", padx=55, pady=25)

def no_mouse_entrar(e):
    e.widget.config(bg="#f7f9fa")

def no_mouse_sair(e):
    e.widget.config(bg="#ffffff")

btn_sim.bind("<Enter>", no_mouse_entrar)
btn_sim.bind("<Leave>", no_mouse_sair)
btn_nao.bind("<Enter>", no_mouse_entrar)
btn_nao.bind("<Leave>", no_mouse_sair)

janela.mainloop()
