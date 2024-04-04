#include <iostream>
#include <fstream>
#include <cmath>
#include <stdexcept>
// Функція для обчислення T(x) з таблиці
double computeT(double x) {
    // Читаємо дані з файлу dat_X_1_1.dat, dat_X1_00.dat або dat_X00_1.dat
    std::ifstream file;
    if (x >= 1)
        file.open("dat_X_1_1.dat");
    else if (x <= -1)
        file.open("dat_X00_1.dat");
    else
        file.open("dat_X1_00.dat");
    double inputX, t, u;
    while (file >> inputX >> t >> u) {
        if (inputX == x)
            return t;
    }
    throw std::runtime_error("Не вдалося знайти значення T(x) у файлі.");
}
// Функція для обчислення U(x) з таблиці
double computeU(double x) {
    // Читаємо дані з файлу dat_X_1_1.dat, dat_X1_00.dat або dat_X00_1.dat
    std::ifstream file;
    if (x >= 1)
        file.open("dat_X_1_1.dat");
    else if (x <= -1)
        file.open("dat_X00_1.dat");
    else
        file.open("dat_X1_00.dat");
    double inputX, t, u;
    while (file >> inputX >> t >> u) {
        if (inputX == x)
            return u;
    }
    throw std::runtime_error("Не вдалося знайти значення U(x) у файлі.");
}
// Функція для обчислення функції fun(x, y, z) за алгоритмами 1, 2 або 3
double computeFun(double x, double y, double z) {
    double fun;
    if (x < 0) {
        fun = 330.0 * (x * y * y * z * z) + (22 * z * x * x * y * y * z * z * y * x * z * y * x * x * y * x * y * z * x * y * z * x * z * y * x * z * y * x * z * x * x * z * y * z * y * x * x * z * z * y * x * x * y * y * y * z * x * y * x * y * z * z);
    } else if (x >= 0.1 && x <= 1.4) {
        fun = (5 * (y / 5) * (y / 5) * (y / 5)) + (0.9 * (830 * (y * z * z * computeT(x) * computeT(x) * computeT(x)) + (5 * (y / 5) * (y / 5) * (y / 5)) * (83891 * (y * z * z * z * z))));
    } else {
        fun = ((x * z * computeU(y) * computeU(y) * computeT(x)) - (3482 * pow(y, 3) * z) - (23622 * pow(x, 3) * z) - (34981 * y * y * x * z));
    }

    return fun;
}
int main() {
    double x, y, z;
    std::cout << "Введіть значення x, y та z: ";
    std::cin >> x >> y >> z;
    try {
        double result = computeFun(x, y, z);
        std::cout << "Результат обчислення fun(x, y, z): " << result << std::endl;
    } catch (const std::runtime_error& e) {
        std::cerr << "Помилка: " << e.what() << std::endl;
    }
    return 0;
}
