# InSem1Project

## Group Name : Titans
## Name : Tanvi Nakum
## Student ID : 202401262

# "THE SNAKE GAME"

```cpp
#include <iostream>
#include <conio.h>
#include <windows.h>
#include <cstdlib>
#include <ctime>

using namespace std;

class Node {
public:
    int x, y;
    Node *next;
    Node(int x, int y) : x(x), y(y), next(nullptr) {}
};

class Snake {
public:
    Node *head;
    Node *tail;

    Snake(int x, int y) {
        head = new Node(x, y);
        tail = head;
    }

    void add(int x, int y) {
        Node *newNode = new Node(x, y);
        newNode->next = head;
        head = newNode;
    }

   void remove() {
        if (head == tail) return;
        Node *temp = head;
        while (temp->next != tail) {
            temp = temp->next;
        }
        delete tail;
        tail = temp;
        tail->next = nullptr;
    }

     bool collision(int x, int y) {
        Node *temp = head;
        while (temp != nullptr) {
            if (temp->x == x && temp->y == y) {
                return true;
            }
            temp = temp->next;
        }
        return false;
    }
};

class Food {
public:
    int x, y;

    Food(int width, int height, Snake *snake) {
        newFood(width, height, snake);
    }

    void newFood(int width, int height, Snake *snake) {
        do {
            x = rand() % width;
            y = rand() % height;
        } while (snake->collision(x, y));
    }
};

enum Direction { STOP = 0, LEFT, RIGHT, UP, DOWN };

class GameBoard {
public:
    int width, height, score;
    Snake *snake;
    Food *food;
    bool gameOver;
    Direction dir;

    GameBoard(int w, int h) : width(w), height(h) {
        score = 0;
        gameOver = false;
        dir = STOP;
        int startX = width / 2;
        int startY = height / 2;
        snake = new Snake(startX, startY);
        food = new Food(width, height, snake);
        snake->add(startX - 1, startY);
        snake->add(startX - 2, startY);
    }

    void Design() {
        system("cls");

        for (int i = 0; i < width + 2; i++) cout << "- ";
        cout << endl;

        for (int i = 0; i < height; i++) {
            for (int j = 0; j < width; j++) {
                if (j == 0) cout << "| ";

                bool printed = false;
                Node *temp = snake->head;
                while (temp != nullptr) {
                    if (temp->x == j && temp->y == i) {
                        cout << "o ";
                        printed = true;
                        break;
                    }
                    temp = temp->next;
                }

                if (!printed) {
                    if (food->x == j && food->y == i)
                        cout << "* ";
                    else
                        cout << "  ";
                }

                if (j == width - 1) cout << "| ";
            }
            cout << endl;
        }

        for (int i = 0; i < width + 2; i++) cout << "- ";
        cout << endl;

        cout << "Score : " << score << endl;
    }

    void Input() {
        if (_kbhit()) {
           char key = _getch();
           //char key;
           //cin>>key;
            switch (key) {
                case 'l': if (dir != RIGHT) dir = LEFT; break;
                case 'r': if (dir != LEFT) dir = RIGHT; break;
                case 'u': if (dir != DOWN) dir = UP; break;
                case 'd': if (dir != UP) dir = DOWN; break;
                case 't': case 'T': gameOver = true; break;
            }
        }
    }

    void Logic() {
        if (dir == STOP) return;

        int newX = snake->head->x;
        int newY = snake->head->y;

        switch (dir) {
            case LEFT:  newX--; break;
            case RIGHT: newX++; break;
            case UP:    newY--; break;
            case DOWN:  newY++; break;
            default: return;
        }

        if (newX >= width || newX < 0 || newY >= height || newY < 0 || snake->collision(newX, newY)) {
            gameOver = true;
            return;
        }

        if (newX == food->x && newY == food->y) {
            score++;
            food->newFood(width, height, snake);
            snake->add(newX, newY);
        } else {
            snake->remove();
            snake->add(newX, newY);
        }
    }
};

int main() {
    srand(time(0));
    GameBoard game(30, 30);
    while (!game.gameOver) {
        game.Design();
        game.Input();
        game.Logic();
        Sleep(100);
    }
    cout << "Game Over! Final Score: " << game.score << endl;
    return 0;
}
