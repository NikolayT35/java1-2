# Отчёт о тестировании <Credit Card Number Validator>

## Краткое описание

<16.08.2020> - <16.08.2020> было проведено <компонентное тестирование, фунциональное,тестирование серого ящика> приложения Credit Card Number Validator.

На тестирование затрачено: <2часа>

В результате тестирования выявлены следующие дефекты:
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/1)
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/2)
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/3)
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/4)
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/5)
* [ссылка на описание дефекта](https://github.com/NikolayT35/java1-2/issues/6)
* Установлена закономерность, валидные номера крат отличные от 16 цифр выдают ошибку,
  вне зависимости от платежной системы.


## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты:
  1. Запустить программу IntekkiJ IDEA 2020.2
  2. Открыть файл Main.Java
  3. Заменить код на указанный ниже
  4. Получить валидные номера карт для тестирования по ссылке ниже
  5. Заменить номер карты указанный в коде в кавычках на нужный
  6. Нажать shift+ctrl+F10
  7. Посмотреть результат в открывшемся окне
  8. Повторить п.5-7 для нужного колличества номеров какрт


В качестве тестовых данных использовались данные:

Доступный код:

  
 ````public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

  long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

     if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
````

* [Источник номеров карт] (freeformatter.com)
* Для всех указнных ниже номеров, ожидаемый результат: Result is OK

  1. VISA
   * 4532210073870051
   * 4916216318643617920
  2.  MASTERCARD
   * 5474192737961541
   * 5514239895348102
  3.  American Express (AMEX):
   * 341137089396665
   * 345756120932976
  4. Discover
   * 6011663988378393
   * 6011539538810173690
  5. Diners Club - Carte Blanche:
   * 30102463284362
   * 30168026225150

Тестирование производилось в следующем окружении:
* WIndows X; 64 bit
* версия Java 10.0.8
* IntekkiJ IDEA 2020.2
