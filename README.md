#include <iostream>
int main() {
    char ch;
    int пробіли = 0, табуляції = 0, нові_рядки = 0;
    while (std::cin.get(ch)) {
        if (ch == ' ') {
            пробіли++;
        } else if (ch == '\t') {
            табуляції++;
        } else if (ch == '\n') {
            нові_рядки++;
        }
    }
    std::cout << "Пробіли: " << пробіли << std::endl;
    std::cout << "Табуляції: " << табуляції << std::endl;
    std::cout << "Нові рядки: " << нові_рядки << std::endl;
    return 0;
}
