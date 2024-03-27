#include <iostream>
// Функція для обчислення факторіалу
int factorial(int n) {
    if (n < 0) {
        throw std::invalid_argument("Неможливо обчислити факторіал від'ємного числа");
    }
    int result = 1;
    for (int i = 2; i <= n; ++i) {
        result *= i;
    }
    return result;
}
int main() {
    try {
        int n;
        std::cout << "Введіть число: ";
        std::cin >> n;
        int result = factorial(n);
        std::cout << "Факторіал " << n << " = " << result << std::endl;
    } catch (std::invalid_argument& e) {
        std::cerr << "Помилка: " << e.what() << std::endl;
    }
    return 0;
}
