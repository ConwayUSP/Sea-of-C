CC = gcc
CFLAGS = -Wall
LIBS = -lraylib -lGL -lm -lpthread -ldl -lrt -lX11

all: game

game: jogo_vida.c
	$(CC) $(CFLAGS) -o game.out jogo_vida.c $(LIBS)

clean:
	rm -f game
