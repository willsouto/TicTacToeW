# Tic Tac Toe W

Jogo da velha(Tic Tac Toe) para 2 jogadores.

Jogo criado em Python com o intuito de ampliar e testar conhecimento adquirido no curso "Complete Python Bootcamp - Milestone 1".



>Obs.: 
> * Para abrir o jogo, baixe o pacote e execute o arquivo 'TicTacToe.exe' contido na pasta 'executavel'.
> * Para rodar o código diretamente, comente ou delete a função 'cls()' em todo o código, para comentar utilize '#'.
> <br/>Ex: #cls()





<img src="https://github.com/willsouto/TicTacToeW/blob/master/img/TicTacToe1.jpg"></img>
<img src="https://github.com/willsouto/TicTacToeW/blob/master/img/TicTacToe2.jpg"></img>
<img src="https://github.com/willsouto/TicTacToeW/blob/master/img/TicTacToe3.jpg"></img>


<pre>
# clearScreen
def cls():
    os.system('cls')

#  funcao para criar tabuleiro zerado
def create_board():
    global board
    board = [[x for x in range(0, 4)] for y in range(0, 4)]
    board[0][0] = ' '

    board[1][0] = 'a '
    board[2][0] = 'b '
    board[3][0] = 'c '

    board[0][1] = ' 1 '
    board[0][2] = ' 2 '
    board[0][3] = ' 3 '

    for i in range(1, 4):
        for y in range(1, 4):
            board[i][y] = ' '

#  funcao para imprimir tabuleiro
def print_board():
    print '\n ~~~~~~~~~~~~~~~~~~~ '
    print '|                   |'
    print '|   '+board[0][0]+' '+board[0][1]+' '+board[0][2]+' '+board[0][3]+'   |'
    print '|   '+board[1][0]+' '+board[1][1]+' | '+board[1][2]+' | '+board[1][3]+'    |'
    print '|   '+'  -----------   |'
    print '|   '+board[2][0]+' '+board[2][1]+' | '+board[2][2]+' | '+board[2][3]+'    |'
    print '|   '+'  -----------   |'
    print '|   '+board[3][0]+' '+board[3][1]+' | '+board[3][2]+' | '+board[3][3]+'    |'
    print '|                   |'
    print ' ~~~~~~~~~~~~~~~~~~~ '

#  funcao para computar jogada
def ins_board(playerins):
    # vez do player
    if playerins % 2 == 0:
        w = 'o'
    else:
        w = 'x'

    x = 0
    y = 1
    # entrada de posicao e check se elemento esta vazio
    while board[x][y] != ' ':
        x = raw_input("\nDigite a linha(a - b - c): ")
        while x != 'a' and x != 'b' and x != 'c':
            x = raw_input("\nAs opcoes de linha sao 'a' ou 'b' ou 'c'.Digite novamente: ")

        y = raw_input("Digite a coluna(1 - 2 - 3): ")
        while y != '1' and y != '2' and y != '3':
            y = raw_input("\nAs opcoes de coluna sao '1' ou '2' ou '3'.Digite novamente: ")

        if x == 'a':
            x = 1
        elif x == 'b':
            x = 2
        elif x == 'c':
            x = 3
        if y == '1':
            y = 1
        elif y == '2':
            y = 2
        elif y == '3':
            y = 3

        if board[x][y] != ' ':
            print("\nEspaco ocupado, escolha novamente!")

    # inseri jogada
    board[x][y] = w


# funcao para definir vez do jogador
def player_turn(player_turn):
    if player_turn % 2 == 0:
        print 'Vez do player: o'
    else:
        print 'Vez do player: x'

# funcao para check de vencedor ou empate
def check_board():
    for x in range(1, 4):

        #  hor/vert
        if board[x][1] == 'x' and board[x][2] == 'x' and board[x][3] == 'x':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"x" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif board[1][x] == 'o' and board[2][x] == 'o' and board[3][x] == 'o':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"o" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif board[x][1] == 'o' and board[x][2] == 'o' and board[x][3] == 'o':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"o" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif board[1][x] == 'x' and board[2][x] == 'x' and board[3][x] == 'x':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"x" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True

        #  direcional cima para baixo
        elif board[1][1] == 'x' and board[2][2] == 'x' and board[3][3] == 'x':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"x" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif board[1][1] == 'o' and board[2][2] == 'o' and board[3][3] == 'o':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"o" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True

        #  direcional baixo para cima
        elif board[3][1] == 'x' and board[2][2] == 'x' and board[1][3] == 'x':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"x" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif board[3][1] == 'o' and board[2][2] == 'o' and board[1][3] == 'o':
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print '"o" vence a partida!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True

        # empate/tabuleiro cheio
        elif plays == 9:
            cls()
            print_board()
            print '\n~~~~~~~~~~~~~~~~~~~~'
            print 'Empatou! \nRestart!'
            print '~~~~~~~~~~~~~~~~~~~~'
            return True
        elif x == 3:
            cls()
            return False

# start
print 'Tic Tac Toe Game!'
cont = 's'

# check para continuar jogo
while cont == 's':
    player = 0

    # escolher primeiro jogador
    while player == 0:
        player = raw_input("\nQual sera o primeiro a jogar('x' ou 'o')?")
        if player == 'x':
            player = 1
        elif player == 'o':
            player = 2
        else:
            player = 0
            print("\nEscolha 'x' ou 'o'!")

    # criar tabuleiro e zerar jogadas
    create_board()
    plays = 0

    # check de vencedor
    while check_board() is False:
        print_board()
        print '\n'
        player_turn(player)
        ins_board(player)
        player += 1
        plays += 1

    # continuar?
    cont = raw_input("\nContinuar jogando('s' ou 'n')?")
    </pre>
