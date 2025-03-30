# Kumeka Bootcamp FAQ
- [Зміст Буткемпу #3](#зміст-буткемпу-3)
- [Загальні посилання та розклад занять](#загальні-посилання-та-розклад-занять)
- [Виконання завдань](#виконання-завдань)
- [Правила обліку успішності учнів](#правила-обліку-успішності-учнів)
- [Правила розіграшу головного призу](#правила-розіграшу-головного-призу)
- [Середовище розробника](#середовище-розробника)
  - [Як швидко познайомитись із TypeScript](#як-швидко-познайомитись-із-typescript)
  - [Як перевірити сумісність процесора із набором інструкцій AVX2](#як-перевірити-сумісність-процесора-із-набором-інструкцій-avx2)
  - [Помилка "Unable to get latest blockhash"](#помилка-unable-to-get-latest-blockhash)
  - [Як вставити фрагмент коду у Discord](#як-вставити-фрагмент-коду-у-discord)

## Зміст Буткемпу #3

- Вступ до криптографії.
- Загальний огляд блокчейнів.
- Взаємодія з блокчейном з клієнтського погляду.
- Транзакції, гаманці та пересиланні SOL.
- Токени, передача токенів.
- Використання Metaplex та створення власного токена.
- Вступ до написання програм, що виконуються всередині блокчейну.
- Програмування блокчейну.
- *NEW!* Frontend для блокчейн-програм.
- *NEW!* Web3 Fullstack для додатків, що використовують блокчейн.

## Загальні посилання та розклад занять

Заняття проходять у Google Meet по понеділкам та середам з 19:00. Всі необхідні посилання наявні у [Google Classroom](https://classroom.google.com/c/NzYwMDIxMDE5NzQ1?cjc=2ugyk43i).  
Учні та викладачі спілкуються у відповідному каналі [Discord](https://discord.gg/4eh4fsBSYX).

## Виконання завдань

Завдання буткемпу поділені на такі категорії:
- завдання з тестами,
- лаба копі-паст код,
- лаба фул складно.

За виконання завдань нараховуються бали у кількості, відповідній до призначеної категорії. Також враховується своєчасніть виконання завдань.

Як правило, завдання з тестами (квізи) потребують лише відповідей на запитання.

Для практичних завдань (лаб) завантажте результати їх виконання до Google Classroom у відповідності із текстом завдання.

**Уважно читайте текст завдання!** Якщо у тексті написано, що має бути 2 скріншоти, то ви маєте додати саме 2. Інше буде помилкою, через яку ви не отримаєте передбачені завданням бали.

**Дата завантаження вважаєтся датою здачі завдання.**

Додатково, для "позанормативних" практичних завдань високої складності (не копі-паст) ви можете додати до відповіді посилання на відповідну папку у вашому персональному репозиторії.  
Для зручності перегляду таких завдань рекомендовано спершу зробити форк [цього репозиторію](https://github.com/ilya-bobyr/solana-ua-bootcamp-2025-03-19).

## Правила обліку успішності учнів

1. Відвідування заняття Google Meet — 1 бал.
2. Виконання квізу — відповідно до кількості балів у завданні, якщо воно складене вчасно, і 50% — якщо ні.
3. Виконання практики — відповідно до кількості балів у завданні, якщо воно складене вчасно, і 50% — якщо ні.
4. Адміністративний бал за коментарі у Діскорд та участь в обговореннях на онлайн-заняттях — не більше 1 балу на тиждень. До уваги беруться влучні запитання або допомога у вирішенні питань та проблем інших учнів.

## Правила розіграшу головного призу

Учні, які складуть мінімум 90% завдань, отримують шанс позмагатися за головний приз буткемпу.  
Набрана кількість балів визначає кількість входжень імені учня до таблиці розіграшу.  
У випадку не цілої кількості балів, вона заокруглюється вниз.  
Володар головного призу визначається онлайн у публічному відео-дзвінку.  
Переможець визначається вибіркою випадкового номеру рядку у таблиці розіграшу за допомогою Wheel of Fortune.  
Переможець має зв'язатися із Kumeka протягом двох робочих днів із дати розіграшу, інакше головний приз буде розіграно повторно.

## Середовище розробника

### Як швидко познайомитись із TypeScript

Навчальний курс Scrimba [на сайті](https://scrimba.com/learn-typescript-c03c/) та у [Youtube](https://www.youtube.com/watch?v=SpwzRDUQ1GI).

### Як перевірити сумісність процесора із набором інструкцій AVX2

Підтримка AVX2 потрібна, зокрема, для запуску `solana-test-validator`.

*Linux*
```
grep -m1 -o 'avx' /proc/cpuinfo
```
Відповідь має містити 'avx'.

*MacOS*
```
sysctl machdep.cpu.features | grep -o 'AVX'
```
Відповідь має містити 'AVX'.

*Windows*
```
wmic cpu get name
```
У пошуковому рядку Chrome пишемо '@gemini avx support назва_процесору'.

### Помилка "Unable to get latest blockhash"

Під час виконання `anchor test` отримую помилку
`Unable to get latest blockhash. Test validator does not look started. `

Переконайтеся, що ваш процесор підтримує набір інструкцій AVX2.

У папці проекту додайте до Anchor.toml
```
[test]
startup_wait = 20000
```
Намагайте не запускати паралельних процесорозалежних задач під час виконання тесту.

### Як вставити фрагмент коду у Discord

Щоб розташувати код в одному рядку з іншим текстом, виділіть його зворотніми лапками `.  
Фрагмент коду можна виділити у блок за допомогою трикратних зворотніх лапок ```.
