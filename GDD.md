# Game Design Document — Евангелие Джекпота

> Written by: [[GameDesigner]]
> Validation: Ready for [[BA]] re-validation after possession-explosion clarification on 2026-05-14
> Last updated: 2026-05-14

---

## Elevator Pitch
**Евангелие Джекпота** — это mobile-first roguelite в портретной ориентации, где посланник Хранителей Вселенной очищает зараженный культом мир, вселяется во врагов и после каждой очищенной комнаты получает случайное благословение от демонического автомата-казино, который сам является святыней врага.

### Рабочая фантазия игрока
Игрок чувствует себя не героем-пророком, а санитаром сломанной веры: он забирает у культа его же инструменты, превращает фанатиков, проповеди, проклятия и игровые автоматы против демона, но постепенно понимает, что Хранители Вселенной тоже не невинны.

### Центральная дизайнерская ставка
Игра должна держаться на двух узнаваемых опорах:
- **Демонический автомат-казино** как основной источник улучшений, риска, юмора и лора.
- **Временное вселение во врагов** как автоматическое контекстное событие: игрок охотится за отмеченным сосудом, а не нажимает отдельную боевую кнопку.

### Выбор боевой модели
Рассматривались варианты:
- **Комнатный roguelike как The Binding of Isaac**: хорошо работает для синергий и боссов, но на телефоне может быть медленнее и требовать много навигации.
- **Арена с волнами и auto-attack**: лучше всего читается на мобильном, быстро запускается, поддерживает короткие сессии.

**Основной выбор: гибрид компактных арен-комнат с auto-attack, ручным движением и автоматическим контекстным вселением.** MVP использует портретное управление без боевых кнопок: игрок двигает героя одним плавающим стиком, атаки происходят автоматически, а вселение срабатывает само при полном заряде рядом с отмеченным сосудом. Auto-attack всегда выбирает ближайшего живого врага или босса в радиусе атаки; при равной дистанции выбирается цель с меньшим текущим HP.

### Краткий elevator pitch для питча
Портретный roguelite про охоту на культ демона-лотереи: двигайся между волнами, заманивай отмеченных врагов под автоматическое вселение и выбирай благословения из автомата, который сам запускается после каждой комнаты.

---

## Core Loop
1. Игрок входит в короткую арену-комнату.
2. Двигается и уклоняется вручную; герой атакует автоматически.
3. Убивает врагов, собирает **индульгенционные жетоны** и заряжает шкалу вселения.
4. Когда шкала вселения заполнена, подводит героя к отмеченному врагу-сосуду, чтобы автоматически вселиться и использовать его способность против волны.
5. После зачистки каждой из 5 боевых комнат автоматически появляется **Священный Автомат Демона**.
6. Автомат сам запускает короткий ролл без ручного spin-input, показывает 3 видимые карты, и игрок выбирает ровно 1 бесплатный стандартный бафф.
7. У игрока есть 3 reroll charges на весь забег; reroll заменяет все 3 видимые стандартные карты и тратит 1 заряд.
8. На втором машинном стопе дополнительно появляется 1 явно отмеченная проклятая сделка: отдельная сильная награда плюс 1 видимое проклятие; reroll стандартных карт ее не меняет.
9. После 5 боевых комнат и 5 машинных стопов игрок выходит на босса зоны.
10. После смерти сохраняется только найденный лор текущего забега; после победы над MVP-боссом открывается стартовый знак **Сломанная Печать** для следующих забегов.
11. Игрок начинает следующий забег с новым знанием, а после первой победы — с одним новым стартовым знаком.

### Core loop в одну строку
**Зачисти комнату, собери жетоны, подведи героя к отмеченному сосуду для автоматического вселения, выбери бесплатный бафф из автоматически запущенного демонического автомата и дойди до босса.**

### Условие поражения
Забег заканчивается, когда здоровье тела героя падает до нуля. Во время вселения физическое тело героя остается на арене как **пустая оболочка**: оно получает сниженный урон, но не бессмертно, поэтому игрок не может бесконечно прятаться внутри врагов.

### Условие победы в зоне
Победа в MVP-зоне наступает после убийства босса Матушки Купонеллы. Награда фиксирована: 1 сюжетный фрагмент и стартовый знак **Сломанная Печать**, который дает +1 начальный индульгенционный жетон в следующих забегах.

### Сюжетная основа
**Хранители Вселенной** — не ангелы и не боги, а бюрократическая космическая служба, которая удерживает реальность от распада. Они следят за законами вероятности, памяти и веры. Если слишком много существ одновременно верят в одну ложь, эта ложь начинает становиться физическим законом.

Герой выбран потому, что он **пустой носитель**: его душа когда-то была неправильно зарегистрирована Хранителями и не закреплена ни за одной верой. Демоническая зараза не может полностью переписать его личность, но через него можно входить в зараженные тела.

Демон веры, **Азартал Святой Шанс**, не просто соблазняет людей. Он заражает мир механизмом "случайного благословения": каждый культист верит, что еще один спин, еще одна молитва, еще одна жертва дадут спасение. Вера работает как зомби-вирус, потому что в этом мире повторенная молитва становится командой реальности. Культ не убеждает людей логикой; он зацикливает их надежду.

Моральный твист: Азартал был создан Хранителями как древний инструмент распределения чудес, но его бросили в мире без надзора. Демон стал питаться отчаянием тех, кому Хранители когда-то отказали. В финале игрок узнает, что "очистить" мир значит не только победить демона, но и сломать систему, где спасение выдается как лотерея.

### Внутренний тон
Мир пугающий, но абсурдный. Проповеди звучат как промо-акции, реликвии похожи на сломанные призы, монахи спорят о процентах выпадения благодати, а святыни требуют "приложить лоб для подтверждения платежа". Юмор черный, но не пародийный: смешное возникает из того, что мир искренне считает нелепость священной.

---

## Platform & Controls
- Platform: Android, mobile-first.
- Orientation: portrait.
- Input: movement-only portrait controls. A floating virtual joystick controls movement; there are no combat buttons for dash or possession in MVP. Slot-machine interaction happens only after combat stops.
- Frame rate target: 60 fps.
- Session length: MVP run target is 7 minutes from spawn to boss result; acceptable range is 6-8 minutes.

### Управление
- Нижняя половина экрана: плавающий виртуальный стик движения. Первое касание в нижней половине ставит центр стика; отпускание останавливает движение героя.
- В MVP нет кнопки рывка, кнопки вселения и дополнительных боевых кнопок.
- Auto-attack включен постоянно. Базовая атака срабатывает каждые 0,75 секунды и выбирает ближайшего живого врага или босса в радиусе 6 игровых метров. Если две цели на одинаковой дистанции, выбирается цель с меньшим текущим HP. Если целей в радиусе нет, герой не атакует.
- После полной зачистки комнаты автомат появляется и запускается сам; игрок взаимодействует только с 3 карточками наград, кнопкой reroll и отдельной проклятой сделкой на втором стопе. В активном бою машинного UI нет.

### Вселение во врагов
- Заряд вселения копится только за убийства: обычный враг дает 25%, дальнобойный проповедник дает 35%, боссовые призывы дают 0%.
- В MVP цель вселения не определяется по HP. Вместо этого wave director создает отмеченных врагов-сосудов.
- Комната 1 не содержит отмеченного сосуда. В комнатах 2-5 появляется ровно 1 отмеченный сосуд на комнату. В босс-комнате отмеченные сосуды не появляются.
- Отмеченным сосудом может быть только слабый культист или быстрый фанатик. Сосуд виден с момента появления: фиолетовый контур, значок над головой и короткий pulse-эффект каждые 1,5 секунды.
- Автоматическое вселение срабатывает без кнопки, если заряд равен 100% и герой находится в радиусе 2,5 игровых метров от отмеченного сосуда 0,35 секунды подряд.
- Если несколько отмеченных сосудов существуют из-за ошибки спавна или debug-сцены, выбирается ближайший к герою; при равной дистанции выбирается цель с меньшим текущим HP.
- Если отмеченный сосуд умер до срабатывания вселения, заряд не тратится, новый сосуд в этой комнате не появляется, и следующая возможность будет только в следующей комнате.
- При старте вселения заряд сбрасывается до 0%. Базовая длительность вселения: 6 секунд. Отдельного cooldown после выхода нет; полная шкала заряда является единственным ограничением.
- Во время вселения стик движения управляет контролируемым врагом, а его способность срабатывает автоматически по ближайшим врагам.
- Тело героя во время вселения остается на месте как пустая оболочка с 60% сопротивления урону. Если оболочка уничтожена, забег заканчивается, даже если игрок сейчас внутри врага.
- Если таймер закончился, комната очищена, или контролируемый враг умер, герой возвращается в оболочку. Базовое вселение уничтожает сосуд без дополнительного жетона, pickup и взрыва. Отмеченный сосуд не взрывается автоматически после выхода; взрыв после выхода доступен только через карту **P03 Последний вздох**.
- Если выбрана **P03 Последний вздох**, взрыв срабатывает при любом выходе из вселения: истечение таймера, зачистка комнаты или смерть контролируемого врага. Взрыв происходит в позиции уничтоженного сосуда, наносит 2 урона всем живым вражеским юнитам в радиусе 2 игровых метров, не наносит урон телу героя, не создает жетоны или pickups и занимает 1 VFX-объект. Если лимит 12 активных VFX уже заполнен, урон все равно применяется, но новый визуальный эффект не создается.

### Типы вселения
| Scope | Тип врага | Способность при вселении | Стратегическая роль |
|---|---|---|---|
| MVP | Слабый культист | Быстрая серия ножевых ударов | Добить плотную группу, дешево и безопасно |
| MVP | Быстрый фанатик | Ускоренное движение и контактный удар по ближайшим врагам | Побег из окружения, сбор жетонов |
| Post-MVP | Святой воин | Щит и таран | Пережить опасную фазу, прорвать броню |
| Post-MVP | Проповедник | Конусная волна лозунгов | Контроль толпы на расстоянии |
| Post-MVP | Мутировавший прихожанин | Взрывная кислотная аура | Рискованный burst-урон |
| Post-MVP | Демонический автомат | Случайный выстрел-символ | Высокий риск, шанс редкого эффекта |
| Post-MVP | Элитный сосуд | Уникальная мини-способность | Самая выгодная цель, требует подготовки |

### Mobile readability
- Не больше 10 обычных врагов одновременно в MVP; элитные враги не появляются в MVP.
- Не больше 18 вражеских снарядов одновременно в MVP.
- Не больше 30 видимых подбираемых жетонов одновременно в MVP; лишние жетоны объединяются в один pickup с суммарным значением.
- Не больше 12 активных VFX-объектов одновременно в MVP, включая взрывы, следы движения, попадания и эффекты проклятий.
- Враги читаются силуэтом: маленькие, быстрые, бронированные, дальнобойные, элитные.
- Улучшения показываются крупными карточками по 3 варианта, без мелкого текста в бою.
- Цвета эффектов закреплены по категориям: атака — красный, защита — синий, мобильность — желтый, вселение — фиолетовый, проклятие — черный/белый.
- Боевых кнопок в MVP нет; в бою используется только плавающий стик движения.

---

## Scenes
| Scene | Purpose |
|-------|---------|
| MainMenu | Start button, текущая зона, базовые разблокировки, доступ к лору |
| Game | Core gameplay loop: арены, волны, жетоны, вселение, автомат, босс |
| GameOver | Итог забега, найденные фрагменты, причина смерти, быстрый restart, переход в меню |

### Дополнительные экраны после MVP
| Scene | Purpose |
|---|---|
| Loadout | Выбор стартового знака Хранителей и косметики |
| LoreArchive | Фрагменты о Хранителях, Азартале и происхождении автомата |
| ShopCosmetic | Только косметика, визуальные темы и отключение рекламы; без продажи силы |
| ZoneMap | Легкая карта прогресса по зонам, без сложной навигации |

### Структура одного забега
- 5 боевых комнат по 45-60 секунд каждая.
- После каждой полной зачистки боевой комнаты автоматически появляется Священный Автомат Демона: комнаты 1, 2, 3, 4 и 5.
- Каждый машинный стоп автоматически запускает короткий ролл, показывает 3 стандартные карты и требует выбрать ровно 1 бесплатный бафф.
- У игрока 3 reroll charges на весь забег; они не восстанавливаются во время забега.
- На втором машинном стопе дополнительно доступна 1 опциональная проклятая сделка.
- 1 босс на 90-120 секунд.

Для MVP используется одна зона: "Приход Первого Спина". В MVP нет карты маршрута, элитных комнат, событий, специальных святынь и автомата внутри активного боя.

---

## Systems
| System | Description | Priority |
|--------|-------------|----------|
| Player movement and auto-combat | Портретное движение, auto-attack, здоровье, получение урона | MVP |
| Arena wave director | Компактные комнаты, волны врагов, выход после зачистки | MVP |
| Demonic slot machine | 5 автоматических post-combat стопов, auto-roll, выбор 1 из 3 бесплатных баффов, 3 reroll charges, 1 опциональная проклятая сделка | MVP |
| Possession | Заряд, отмеченный сосуд, автоматический proximity-trigger, временный контроль врага, пустая оболочка героя | MVP |
| Boss encounter | Один босс зоны с двумя фазами и наградой | MVP |
| Run results | Смерть/победа, найденный лор, быстрый restart | MVP |
| Simple meta unlock | После первой победы открывается стартовый знак "Сломанная Печать" | MVP |
| Expanded meta progression | Новые автоматы, стартовые знаки, косметика | Post-MVP |
| Full biome chain | 4-6 зон с уникальными врагами и боссами | Post-MVP |
| Ethical monetization | Косметика, battle pass без силы, rewarded ads без влияния на баланс | Post-MVP |

### Демонический автомат-казино
Автомат называется **Священный Автомат Демона**. Для культа это алтарь, исповедальня и лотерея спасения. Для героя это украденный инструмент, который перераспределяет силу верующих против них.

#### Валюта
- **Индульгенционные жетоны**: единственная MVP-валюта-пикап. Обычный враг имеет 35% шанс уронить 1 жетон, дальнобойный проповедник всегда роняет 1 жетон, босс роняет 5 жетонов только для итогового экрана. Жетоны не требуются для стандартного room-clear баффа, не тратятся на обычный ролл и не тратятся на reroll в MVP.
- **Reroll charges**: отдельный run-resource, не валюта. Игрок начинает забег с 3 зарядами reroll, тратит 1 заряд при каждом reroll и не может восстановить заряды во время забега.
- **Заряд вселения**: отдельная боевая шкала, не валюта и не тратится в автомате.
- **Души сдачи** и **Кредит веры** переносятся в Post-MVP.

#### Где появляется автомат
- В MVP автомат появляется автоматически после каждой полной зачистки боевой комнаты: комнаты 1, 2, 3, 4 и 5.
- Автомат появляется только когда все враги мертвы, вражеские снаряды исчезли, и combat-state выключен.
- Игрок не подходит к автомату и не нажимает manual spin. После появления автомат сам проигрывает короткую roll-анимацию 0,8-1,2 секунды.
- Стандартный room-clear ролл стоит 0 жетонов на всех 5 стопах. Нехватка жетонов не блокирует награду: стандартный бафф всегда бесплатный и гарантированный.
- После auto-roll автомат показывает 3 видимые стандартные карты из `MVP reward pool`; игрок обязан выбрать ровно 1 карту, чтобы продолжить.
- В одном забеге игрок может получить до 5 стандартных баффов: по 1 после каждой из 5 боевых комнат.

#### Типы выпадений
| Категория | MVP-награды | Роль |
|---|---|---|
| Атака | 4 карты: Святая отдача, Кадило очереди, Ритм барабана, Острый купон | Ускоряет зачистку |
| Защита | 3 карты: Печать возврата, Запасной нимб, Милость кассира | Стабилизирует забег |
| Мобильность | 2 карты: Паломнический шаг, Скидка на бегство | Помогает выживать |
| Вселение | 3 карты: Душа напрокат, Нотариальная одержимость, Последний вздох | Делает ключевую механику глубже |
| Проклятая сделка | 1 фиксированная сделка на втором автомате: Фанатичный кредит | Создает контролируемый риск |

#### Риск, reroll и честность
- Стандартный auto-roll всегда показывает 3 видимые карты наград, и игрок выбирает ровно 1.
- Карты выбираются случайно из 12 стандартных MVP-наград без дублей внутри одного показа; уже выбранные в этом забеге карты повторно не появляются.
- Нажатие **Reroll** заменяет все 3 текущие видимые стандартные карты, тратит 1 reroll charge и снова соблюдает правило без дублей внутри показа. Новый показ не повторяет 3 только что замененные карты, уже выбранные карты не возвращаются. Если reroll charges равны 0, кнопка неактивна.
- Reroll стандартных карт не меняет, не скрывает и не перебрасывает проклятую сделку второго стопа.
- Стандартный auto-roll никогда не выдает проклятие.
- На втором машинном стопе дополнительно появляется одна кнопка **Проклятая сделка**. Она бесплатна, не заменяет гарантированный стандартный бафф, требует отдельного подтверждения и показывает точную пару: награда + проклятие.
- Единственная MVP-проклятая сделка — **Фанатичный кредит**: немедленно получить cursed bonus **Острый долг** (+1 урон базовой атаки до конца забега), но максимальное HP героя уменьшается на 1 до конца забега. Это не стандартная карта и не считается одним из 5 стандартных баффов.
- В MVP за забег можно взять максимум 1 проклятие.
- Машинные стопы 1, 3, 4 и 5 не предлагают проклятую сделку.
- Реальные деньги никогда не покупают спины, силу, шансы или жетоны.
- Rewarded ads могут дать только косметический reroll внешнего вида награды или небольшую внебоевую валюту после забега, не влияющую на текущий run.

### Прогрессия внутри забега
- Игрок получает до 5 стандартных наград за забег, по одной после каждой боевой комнаты.
- Стандартная награда бесплатна и гарантирована независимо от количества жетонов.
- Игрок начинает с 3 reroll charges на весь забег; reroll charges не восстанавливаются.
- На втором машинном стопе игрок может дополнительно принять одну проклятую сделку, не теряя гарантированный стандартный бафф.
- Каждая награда принадлежит одной MVP-категории: атака, защита, мобильность, вселение.
- Вселение меняется только через конкретные награды: +1 секунда длительности, больший proximity-trigger, взрыв после выхода.

### Прогрессия между забегами
- До первой победы между забегами сохраняются только открытые фрагменты лора.
- После первой победы над Матушкой Купонеллой открывается один стартовый знак: **Сломанная Печать**.
- **Сломанная Печать** дает +1 начальный индульгенционный жетон при старте нового забега; этот жетон влияет только на итоговый счет/будущую экономику и не нужен для стандартных MVP-баффов.
- Постоянные стат-бонусы, новые типы автоматов, косметика и дополнительные стартовые знаки переносятся в Post-MVP.

### MVP reward pool
| ID | Категория | Карта | Эффект |
|---|---|---|---|
| A01 | Атака | Святая отдача | Каждая третья базовая атака отталкивает цель на 1 игровой метр |
| A02 | Атака | Кадило очереди | Базовая атака дополнительно задевает второго ближайшего врага в радиусе 2 игровых метров от цели |
| A03 | Атака | Ритм барабана | Интервал базовой атаки уменьшается с 0,75 до 0,68 секунды |
| A04 | Атака | Острый купон | Базовая атака наносит +1 урон |
| D01 | Защита | Печать возврата | При входе в комнату герой получает щит на 2 секунды |
| D02 | Защита | Запасной нимб | Максимальное HP героя увеличивается на 1 и текущее HP увеличивается на 1 |
| D03 | Защита | Милость кассира | После каждого автомата герой лечит 1 HP, не выше максимума |
| M01 | Мобильность | Паломнический шаг | Скорость движения героя увеличивается на 10% |
| M02 | Мобильность | Скидка на бегство | Когда HP героя падает до 2 или ниже, скорость движения увеличивается на 20% на 4 секунды; срабатывает максимум 1 раз за комнату |
| P01 | Вселение | Душа напрокат | Длительность вселения увеличивается с 6 до 7 секунд |
| P02 | Вселение | Нотариальная одержимость | Радиус автоматического вселения увеличивается с 2,5 до 3,0 игровых метров |
| P03 | Вселение | Последний вздох | Только если эта карта выбрана: при любом выходе из вселения сосуд взрывается, наносит 2 урона всем живым вражеским юнитам в радиусе 2 игровых метров, не повреждает тело героя, не создает жетоны или pickups и занимает 1 VFX-объект; при заполненном VFX-лимите урон применяется без нового визуального эффекта |

### MVP cursed deal
| Scope | Сделка | Награда | Проклятие |
|---|---|---|---|
| MVP | Фанатичный кредит | Немедленно получить cursed bonus **Острый долг**: базовая атака наносит +1 урон до конца забега; это не стандартная карта и не занимает один из 5 обычных выборов | Максимальное HP героя уменьшается на 1 до конца забега |

### Post-MVP reward examples
| Категория | Улучшение | Эффект |
|---|---|---|
| Проклятие | Десятина боли | Каждый спин лечит героя, но снижает максимум HP до конца зоны |
| Джекпот | Джекпот безумия | Все характеристики растут, враги становятся быстрее |
| Джекпот | Три нимба | Три случайные награды сразу, но один будущий автомат будет проклят |
| Рискованная сделка | Бесплатная благодать | Спин стоит 0, но результат нельзя отменить |
| Рискованная сделка | Возврат без чека | Вернуть последнее улучшение за жетоны и получить проклятие |

### Биомы и зоны
| Scope | Зона | Визуальный стиль | Враги | Опасности | Босс/мини-босс | Награды |
|---|---|---|---|---|---|---|
| MVP | Зараженная деревня "Приход Первого Спина" | Гнилые домики, вывески-молитвы, алтарные автоматы на площади | культисты, фанатики, проповедники | колокольные волны, лужи воска, рекламные проповеди | Матушка Купонелла | сюжетный фрагмент и стартовый знак "Сломанная Печать" |
| Post-MVP | Казино-монастырь "Обитель Трех Барабанов" | Монастырские арки, неоновые витражи, барабаны вместо икон | монахи-дилеры, святые воины, автоматы-враги | вращающиеся пола, ловушки-монеты, двери за жетоны | Брат Барабаний | защитные улучшения |
| Post-MVP | Катакомбы проигравших душ | Кладбище, кассы индульгенций, кости как жетоны | мертвые должники, призраки, проповедники | долговые цепи, могилы-ловушки, налог на лечение | Индульгент Проигравших | проклятые сделки, усиления вселения |
| Post-MVP | Собор демонической лотереи | Огромный собор с лототроном вместо алтаря | проповедники, элитные сосуды, фанатики | падающие шары-номера, зоны "выигрыша" и "штрафа" | Архирекламщик Вельзевит | джекпот-улучшения, редкие синергии |
| Post-MVP | Небесная канцелярия Хранителей | Бело-золотой офис вне мира, печати, очереди душ, сломанные формы | архивариусы, печатники, стражи вероятности | бюрократические барьеры, отмена эффектов, задержка кнопок | Секретарь Ноль-Ноль | стартовые знаки Хранителей, лор |
| Post-MVP | Тронный зал Азартала | Красно-черная капелла с бесконечными автоматами и живыми барабанами | все классы врагов, усиленные автоматы | случайные правила комнаты, проклятые джекпоты | Азартал Святой Шанс | финальный выбор, окончание арки |

### Враги
| Scope | Класс | Поведение | Атаки | Контр-игра | Награда за вселение |
|---|---|---|---|---|---|
| MVP | Слабый культист | Идет группой, давит числом | короткий удар ножом, бросок свечи | держать дистанцию, использовать отталкивание | быстрые удары, безопасное добивание |
| MVP | Быстрый фанатик | Короткими ускорениями обходит игрока | прыжок, саморазгон | ждать ускорение, уходить в сторону | ускоренное движение и контактный урон |
| MVP | Дальнобойный проповедник | Держится краев арены | конус лозунгов, проклятый снаряд | быстро сближаться и уклоняться от конуса | нет вселения в MVP |
| Post-MVP | Бронированный святой воин | Медленно наступает, закрывает других | щитовой таран, удар колоколом | заходить сбоку, использовать взрывы | щит, таран, временная броня |
| Post-MVP | Мутировавший прихожанин | Непредсказуемо меняет форму | плевок воском, кислотная аура | не стоять рядом долго | аура урона и взрыв при выходе |
| Post-MVP | Демонический автомат | Стоит как объект, потом оживает | снаряды-символы, притяжение жетонов | ломать между волнами, избегать линий | случайный символ-выстрел, шанс мини-спина |
| Post-MVP | Элитный сосуд веры | Редкий сильный враг с подсветкой | комбинированные атаки | копить заряд вселения специально под него | уникальная способность комнаты |

### Боссы
| Scope | Босс | Образ и роль | Фазы | Уникальная механика | Награда |
|---|---|---|---|---|---|
| MVP | Матушка Купонелла | Староста деревни, святая промо-акций, лицо закрыто стопкой купонов | 1: призывает культистов; 2: режет арену скидочными лентами | "Акция дня": каждые 20 секунд создает одну опасную красную ленту и одну безопасную золотую зону | сюжетный фрагмент и стартовый знак "Сломанная Печать" |
| Post-MVP | Брат Барабаний | Монах-казначей с тремя барабанами вместо туловища | 1: вращает паттерны снарядов; 2: меняет правила комнаты каждые 10 секунд | Игрок может вселиться в один барабан и остановить паттерн | защитное улучшение |
| Post-MVP | Индульгент Проигравших | Мертвый сборщик долгов в ризе из квитанций | 1: вызывает должников; 2: крадет жетоны с пола | Чем больше жетонов носит игрок, тем сильнее атаки босса | система рискованных сделок |
| Post-MVP | Архирекламщик Вельзевит | Проповедник-ведущий с микрофоном-кадилом | 1: лозунги-снаряды; 2: арена делится на зоны "выигрыш/штраф" | Безопасные зоны меняются как рекламные баннеры | редкое джекпот-улучшение |
| Post-MVP | Секретарь Ноль-Ноль | Представитель Хранителей, белая маска и бесконечная печать | 1: отменяет часть баффов; 2: вызывает архивные копии врагов | Проверяет, насколько игрок зависим от случайных благословений | стартовый знак Хранителей |
| Post-MVP | Азартал Святой Шанс | Финальный демон, живой автомат с нимбом из барабанов и лицами верующих на символах | 1: честная лотерея атак; 2: заставляет выбирать между силой и проклятием; 3: раскрывает связь с Хранителями | Босс предлагает "бесплатные" благословения во время боя, каждое меняет паттерны и цену победы | финальный выбор: уничтожить автомат, передать его Хранителям или освободить веру от обеих сторон |

---

## Art Style
- Style: stylized dark cartoon with grotesque religious-casino motifs; readable silhouettes over realism.
- Color palette: deep charcoal `#17151A`, old gold `#C89B3C`, wax white `#E8DCC2`, infected crimson `#9E2431`, toxic green `#68B66B`, void violet `#6D4BC3`.
- Character: худой посланник в коротком плаще, с пустой маской вместо лица и печатью Хранителей на груди; силуэт простой, чтобы читался на маленьком экране.
- Background: темные арены с яркими интерактивными акцентами: жетоны, символы автомата, проклятия и зоны опасности должны быть заметнее декора.

### Визуальные правила
- Герой всегда светлее фона и имеет холодный контур.
- Враги культа имеют теплые грязные цвета: красный, золото, воск, ржавчина.
- Хранители используют стерильный белый, небесно-синий и золотые печати.
- Азартал и автоматы используют красный, черный, золото и фиолетовый.
- UI автомата должен выглядеть как предмет мира: барабаны, рычаг, символы, трещины, живые глаза, но взаимодействие остается простым и читаемым.

### FLUX-ready art direction
Ключевая формула промптов: **dark whimsical cult roguelite, grotesque sacred casino machine, stylized mobile game asset, readable silhouette, old gold and crimson accents, black humor, high contrast, no photorealism**.

### Атмосферные референсы и уроки
- **Cult of the Lamb**: взять контраст милого силуэта и жуткой темы; адаптировать через Писаря и абсурдных культистов, не копируя деревню/культ-менеджмент.
- **The Binding of Isaac**: взять гротеск, комнатную ясность и синергии; не копировать управление и темп.
- **Vampire Survivors**: взять auto-attack, читаемый хаос и короткий цикл усилений; не превращать игру в чистый swarm-survivor.
- **Hades**: взять нарратив после смерти и постепенное раскрытие мира; не копировать объем диалогов для MVP.
- **Slay the Spire / Balatro**: взять честную случайность, рискованные сделки и удовольствие от build-синергий; не использовать реальные gambling-механики.
- **Dead Cells**: взять ощущение мастерства через уклонение, позиционирование и босс-паттерны; не усложнять мобильное управление.

---

## Audio
- BGM: мрачная сказочная музыка с органом, сломанной шарманкой, тихим хором и ритмом игровых барабанов.
- SFX: attack hit, movement boost, possession marker pulse, possession start/end, token pickup, slot auto-roll, reroll, jackpot, curse, boss phase shift.

### Музыкальные слои
- Обычная комната: низкий пульс, редкие колокольчики, приглушенный хор.
- Автомат: барабаны, монеты, шепот "еще один спин", короткий музыкальный sting результата.
- Босс: орган, тяжелый барабан, резкие рекламные интонации в голосовых вставках.
- Небесная канцелярия: стерильный хор, печатная машинка, офисный звонок, почти смешная бюрократическая чистота.

### Голос и юмор
Голоса не должны быть длинными. Лучше короткие фразы:
- "Благодать не возвращается."
- "Ваша молитва очень важна для нас."
- "Джекпот любит терпеливых."
- "Хранители уже рассмотрели вашу смерть."

---

## MVP Scope
> What must work for the game to be "playable in 3 sessions"?

- [ ] One portrait arena zone with exactly 5 combat rooms, 5 automatic post-combat machine stops, 1 boss, and a 6-8 minute playable run.
- [ ] Movement-only portrait controls: one floating joystick, no dash button, no possession button, and no extra combat buttons.
- [ ] Player movement, deterministic nearest-target auto-attack, health, damage, death, and restart.
- [ ] Three enemy classes: weak cultist, fast fanatic, ranged preacher.
- [ ] Automatic possession of marked weak cultist and fast fanatic vessels using full charge, 2.5-meter proximity trigger, 6-second duration, empty-body fail rule, and buff-only exit explosion through **P03 Последний вздох**.
- [ ] Demonic slot machine after every cleared combat room, rooms 1-5, with auto-roll, 12 standard reward cards, 3 total reroll charges, and 1 optional cursed deal only on the second machine stop.
- [ ] One boss, Матушка Купонелла, with two phases.
- [ ] Run results screen with collected tokens, one lore fragment, unlocked start sign status, and quick restart.
- [ ] One concrete meta reward: after first boss victory, unlock **Сломанная Печать** for +1 starting token.

### MVP acceptance criteria
- On a 1080x1920 Android test screen, the floating joystick is visible while touched, has a touch area of at least 160x160 px, and no combat buttons except the movement joystick are visible during combat.
- Auto-attack selects the nearest living enemy or boss within 6 gameplay meters; when two targets are equally distant, the target with lower current HP is selected.
- A full MVP run contains 5 combat rooms, 5 automatic machine stops after rooms 1-5, and 1 boss encounter.
- During combat, the game never exceeds 10 enemies, 18 enemy projectiles, 30 visible pickups, or 12 active VFX objects at the same time.
- The machine appears automatically after every combat room clear and never during active combat.
- The machine auto-rolls without a manual spin button or walk-up interaction.
- Each machine stop shows 3 readable standard buff cards and lets the player select exactly 1 card.
- Standard buffs are free and guaranteed; token count never blocks the normal room-clear buff.
- Player starts each run with 3 total reroll charges; reroll replaces all 3 offered standard cards and decreases reroll count by 1.
- Standard machine cards are drawn from the 12-card `MVP reward pool` without duplicates inside one 3-card offer, and already selected standard cards never appear again in the same run.
- The second machine stop shows the optional **Фанатичный кредит** cursed deal; accepting it grants **Острый долг**, lowers max HP by 1 until run end, and disables further cursed deals for the run.
- Rerolling normal cards does not reroll or change the cursed deal.
- Player can receive up to 5 standard buffs per run, one after each combat room.
- Rooms 2-5 each spawn exactly 1 visibly marked possession vessel; room 1 and the boss room spawn 0 possession vessels.
- Possession starts automatically only when charge is 100% and the hero remains within 2.5 gameplay meters of a marked possession vessel for 0.35 seconds.
- If the marked vessel dies before possession starts, charge remains unchanged and no replacement vessel appears in the same room.
- If the hero body reaches 0 HP during possession, the run ends immediately and shows the GameOver screen.
- Without **P03 Последний вздох**, possession ending by timer, room clear, or controlled-enemy death destroys the vessel with no explosion VFX, no area-damage event, and no extra token or pickup.
- With **P03 Последний вздох**, possession ending by timer, room clear, or controlled-enemy death creates exactly 1 explosion at the vessel position, deals 2 damage only to enemy units within 2 gameplay meters, does not damage the hero body, and creates no extra token or pickup.
- After death or victory, the GameOver screen shows a restart button within 3 seconds.
- After the first boss victory, the next run starts with **Сломанная Печать** active and +1 starting token.

### Коммерческое позиционирование
1. **"Vampire Survivors meets cursed slot machines"** — для игроков, которые хотят быстрые мобильные забеги и смешные синергии.
2. **"A dark cult roguelite built for portrait play"** — акцент на мобильность, стиль и короткие сессии.
3. **"Possess enemies, rig the demon's machine, break the gospel of chance"** — акцент на уникальные механики и сюжетный крючок.

### 10 MVP decisions before prototype
1. Auto-attack targets the nearest living enemy or boss within 6 gameplay meters; equal-distance ties target the lower-HP target.
2. Combat rooms target 45-60 seconds each; the full MVP run target is 7 minutes with an acceptable 6-8 minute range.
3. Possession requires 100% charge and proximity to a visibly marked vessel; HP threshold and manual possession button are not used in MVP. Default possession exit does not explode; only **P03 Последний вздох** adds exit explosion.
4. The hero body has 60% damage resistance during possession, but death of the body immediately ends the run.
5. A run contains 5 automatic machine stops: one after each cleared combat room, before the boss transition.
6. Standard machine rewards are free and guaranteed; tokens are collected for score/future economy, not spent on normal MVP buffs.
7. Standard machine auto-rolls always show 3 visible rewards and require the player to choose exactly 1.
8. Player starts with 3 total reroll charges; reroll replaces all 3 visible standard cards, selected cards never return, and charges do not refresh during the run.
9. A run can contain at most 1 curse: **Фанатичный кредит**, available only on machine stop 2 and unaffected by normal-card rerolls.
10. MVP uses movement-only portrait controls, no combat buttons, no pet/helper system, and a 10-enemy simultaneous cap for readability.

## Out of Scope (v1)
- Full 6-zone campaign.
- More than one playable hero.
- Manual dash, manual possession button, and alternate two-thumb action mode.
- Complex procedural map with branching routes.
- Full narrative dialogue system.
- Souls, Credit Faith, multiple machine types, reroll refresh sources, combat-time machine interaction, elite rooms, and in-run shops.
- Pet/helper companion systems, Писарь, helper attacks, helper commands, helper pickups, helper reward cards, and helper SFX.
- Post-MVP enemies, possession types, biomes, bosses, jackpots, and risk-deal cards listed outside the MVP tables.
- Online leaderboards, multiplayer, clans, social systems.
- Real-money power purchases, paid run upgrades, paid slot spins, paid odds boosts.
- Aggressive ads, forced ads inside a run, gambling monetization.
- Battle pass implementation.
- Advanced analytics and live ops balancing.
- Localization beyond the working design language.

### Этичная монетизация после MVP
- Косметические облики героя, автоматов и жетонов.
- Визуальные темы зон, не меняющие баланс.
- Battle pass только с косметикой, лором и декоративными эффектами.
- Покупка "remove ads".
- Rewarded ads только после забега и только для необязательных бонусов, не влияющих на текущий run или шанс автомата.

---

> [[BA]]: add clarification questions below this line after review.

## BA Review — 2026-05-12
**Validation status: BLOCKED.** The GDD has enough concept direction to continue design, but it is not approved for [[Architect]] yet. Several MVP requirements are still ambiguous, and the "10 вопросов перед прототипом" section contains unresolved decisions that directly affect implementation.

### Passes
- Narrative questions are answered: the GDD defines the Хранители Вселенной, why the hero was chosen, what Азартал is, why faith behaves like a virus, who the final boss is, and the moral twist.
- The demonic slot machine is framed as an in-world gameplay and lore system, not real-money gambling.
- Mobile-first intent is present: Android, portrait orientation, short sessions, readable silhouettes, limited text during combat, and large interaction targets.
- The MVP direction is feasible if scope is reduced to one arena zone, one boss, three enemy classes, one helper, possession, and a simplified slot-machine reward flow.

### Blocking Logic Gaps
1. **Auto-attack targeting is unresolved.** The GDD says attacks target the nearest or priority enemy. MVP must pick one rule, for example nearest enemy within range, with a deterministic tie-breaker.
2. **Run length and room pacing conflict.** The GDD lists 6-10 minutes for a short run segment, 12-18 minutes for a full early-zone run, and 5-7 MVP rooms. MVP needs one target duration and expected room duration.
3. **Slot-machine flow is ambiguous.** The GDD mentions safe spin, risky spin, helper upgrade, cursed deal, every second room, selected rooms, and every third machine giving three rewards. MVP needs one exact machine flow.
4. **Curses and negative results need boundaries.** The GDD says normal spins do not give negative effects without warning, but curse categories are part of rewards. Define which player action can produce a curse and the maximum curse count in MVP.
5. **Possession targeting has two rules.** The GDD says enemies are available at 40% HP or when marked by a special effect. MVP needs one trigger, plus behavior when the target dies, the timer ends, the room clears, or the hero body is killed.
6. **Helper behavior is too broad.** The GDD lists attack, pickup, roles, mutations, and an active command. MVP should specify whether Писарь is fully automatic or has exactly one active command.
7. **Currency economy is over-scoped.** Индульгенционные жетоны, Души сдачи, and Кредит веры are all defined, but MVP needs either one currency or exact rules for all three.
8. **Meta progression is not implementation-ready.** The GDD mentions permanent upgrades, new automats, new helpers, starter signs, cosmetics, lore, and placeholder progression. MVP needs one concrete post-run unlock only.
9. **Boss reward affects systems outside MVP.** Матушка Купонелла rewards a permanent machine type, but only one machine type is needed in MVP. Define the boss reward as lore, a replay unlock, or a simple upgrade.
10. **Success criteria are not observable enough.** "Игрок понимает управление" and "смерть воспринимается как повод быстро начать снова" are useful goals, but QA needs measurable criteria such as buttons visible, restart available within N seconds, first machine appears before N seconds, and possession can be triggered N times.

### Mobile Feasibility Risks
1. **One-thumb claim conflicts with control layout.** The GDD places joystick on the left and action buttons on the right, which is two-thumb play. Decide whether MVP targets one-thumb or two-thumb portrait controls.
2. **Combat UI may be overloaded.** Movement, dash, possession, helper command, machine interaction, helper behavior, 12-16 enemies, and projectiles may crowd a portrait screen. MVP should remove the helper command or lower the enemy cap.
3. **Enemy count needs a device-safe cap.** For MVP, define a maximum simultaneous count for normal enemies, elite enemies, enemy projectiles, pickups, and active VFX.
4. **Slot-machine UI is feasible only outside active combat.** BA recommends MVP machine interaction happens after room clear, not while enemies are attacking.

### Required Clarifications Before Approval
1. What is the exact MVP control scheme: one-thumb portrait, or two-thumb portrait?
2. What is the exact auto-attack target rule?
3. What is the MVP room count and total run duration target?
4. When exactly does the slot machine appear in the MVP?
5. What does one MVP machine interaction contain: one random result, three choices, reroll, or safe/risky branch?
6. What is the MVP possession trigger: 40% HP, marked target, or another single rule?
7. What are the fail/boundary rules for possession?
8. Is Писарь automatic in MVP, or does he require a command button?
9. Which currencies exist in MVP, and what are their sources and spends?
10. What single meta-progression reward exists in MVP?

### BA Decision
Route back to [[GameDesigner]] for a focused GDD revision. Do not route to [[Architect]] until the clarifications above are resolved directly in [[GDD]].

## BA Re-validation — 2026-05-12
**Validation status: BLOCKED.** The revision fixed the major logic gaps around controls, targeting, room pacing, slot-machine timing, possession boundaries, helper automation, currency scope, and meta reward. The game is now directionally feasible as a portrait Android game. It is not approved for [[Architect]] yet because several implementation-facing contradictions remain.

### Portrait Feasibility Verdict
**Good for portrait, with two-thumb controls.** The current control model is feasible because movement is on the left, dash/possession are on the right, the helper is automatic, and the slot-machine UI appears after combat. The design should not claim one-thumb play for MVP.

### Remaining Blocking Issues
1. **Reward pool mismatch.** MVP says the slot machine has 15 standard reward cards, but the examples section defines only 10 standard non-curse rewards. Either define all 15 exact card names/effects or reduce the MVP machine pool to the exact listed cards.
2. **Cursed deal is not exact enough.** MVP says there is 1 optional cursed deal on the second machine, but the GDD does not define the exact pair of reward and curse. Pick one exact deal, for example `+1 damage now; all later standard spins cost +2 tokens`.
3. **MVP and Post-MVP enemies are mixed in implementation tables.** MVP scope says 3 enemy classes and possession for 2 classes, but the possession/enemy tables list holy warriors, mutants, machines, elite vessels, and other possession rewards without marking them Post-MVP. Split or label those rows so Architect does not task them for MVP.
4. **Portrait performance caps are incomplete.** The GDD caps enemies at 10 but does not cap enemy projectiles, pickups, or active VFX. For a portrait Android MVP, add explicit caps for these objects.

### Required Fixes Before Approval
1. Define the exact MVP reward pool used by the 3-card machine UI.
2. Define the exact MVP cursed deal.
3. Mark non-MVP enemy, possession, boss, jackpot, reroll, and risk-deal examples as Post-MVP.
4. Add explicit portrait-screen caps for simultaneous enemy projectiles, visible pickups, and active VFX.

### BA Decision
Route back to [[GameDesigner]] for a small cleanup pass. The core concept and portrait control model are acceptable; remaining work is requirements cleanup, not a redesign.

## BA Cleaned Re-validation - 2026-05-13
**Validation status: APPROVED for [[Architect]] routing.** The cleanup pass resolved the remaining implementation blockers from `BA Re-validation - 2026-05-12`.

### Confirmed
- The `MVP reward pool` contains exactly 15 standard reward cards: A01-A04, D01-D03, M01-M02, H01-H03, and P01-P03.
- The single MVP cursed deal is deterministic: `Fanatichny kredit` grants one reward resolution, A04 or A03 if A04 was already selected, and applies one curse: all later standard spins in the run cost +2 tokens.
- MVP and Post-MVP content are separated in the reward, enemy, possession, biome, and boss tables. Architect should scope only rows marked `MVP` and the `MVP reward pool`.
- Portrait performance caps are implementation-ready: 10 enemies, 18 enemy projectiles, 30 visible pickups, and 12 active VFX objects during combat.

### BA Decision
No blocking ambiguity remains for the MVP. Route [[GDD]] to [[Architect]] for implementation task breakdown.

## BA Control-Model Reopen - 2026-05-13
**Validation status: BLOCKED.** The human owner rejected the current two-thumb portrait action layout as uncomfortable and clarified a new preferred MVP direction.

### Confirmed Direction From Human Owner
- Keep portrait orientation, but reduce active combat buttons.
- Player should control movement; attacking should be fully automatic.
- Delete manual dash from MVP.
- Auto-attack should target the nearest valid enemy, including bosses.
- Possession should be automatic/contextual: levels spawn special valid possession enemies, those enemies are visibly marked, and possession triggers when the player is near a marked valid target.

### Remaining Requirements Gap
The current GDD still depends on a right-side dash button and a right-side possession button. Dash is now explicitly out, and possession is no longer a manual button. GameDesigner must rewrite the MVP control model around movement-only combat input, full auto-attack, and automatic possession of marked valid enemies. The revision must define the exact trigger range, marker behavior, spawn rule for possession-valid enemies, and boundary behavior when multiple marked enemies are near or the target dies.

### BA Decision
Do not route to [[Architect]] yet. Route back to [[GameDesigner]] for a focused GDD revision that simplifies controls and updates every affected MVP requirement, acceptance criterion, and out-of-scope line.

## GameDesigner Control Revision - 2026-05-13
**Revision status: READY FOR [[BA]] re-validation.** The MVP control model has been rewritten around comfortable portrait play.

### Locked Changes
- Combat input is movement-only: one floating joystick, no dash button, no possession button, no helper command button.
- Auto-attack is always on and targets the nearest living enemy or boss within 6 gameplay meters.
- Dash has been removed from MVP controls, combat requirements, rewards, audio, and acceptance criteria.
- Possession is automatic/contextual: rooms 2-5 each spawn exactly 1 visibly marked weak cultist or fast fanatic vessel.
- Automatic possession requires 100% charge and 0.35 seconds within 2.5 gameplay meters of the marked vessel.
- Possession has no separate cooldown; spending full charge is the gate.

### BA Handoff Note
BA should re-check that the revised controls, possession rules, MVP reward pool, enemy table, audio, MVP scope, and acceptance criteria no longer contradict the movement-only control model.

## BA Control and Machine Re-validation - 2026-05-13
**Validation status: BLOCKED.** The revised movement-only control model is comfortable enough for portrait MVP, but the casino-machine cadence does not match the human owner's stated expectation that the machine appears in each room and gives the player buffs.

### Passes
- Portrait comfort is now acceptable for MVP: combat uses one floating joystick, no dash button, no possession button, no helper command button, automatic attack, and automatic marked-vessel possession.
- Auto-attack is implementation-ready: nearest living enemy or boss within 6 gameplay meters, lower-HP tie-breaker.
- Automatic possession is implementation-ready enough for task breakdown: marked vessels, charge requirement, proximity trigger, no manual button, no separate cooldown, target-death behavior, and empty-body fail rule are defined.
- The MVP reward pool still has exactly 15 standard cards, and no standard card depends on manual dash.

### Blocking Issue
The GDD does **not** clearly say the casino machine appears in each room. It repeatedly says the machine appears only 3 times:
- Core loop: after combat rooms 2 and 4, plus before the boss.
- Run structure: machine after room 2, after room 4, and after room 5.
- Machine section: exactly 3 appearances after rooms 2, 4, and 5.
- MVP scope and acceptance criteria: 3 post-combat machine stops after rooms 2, 4, and 5.

This conflicts with the requested direction: the casino machine should appear in each room and give the player buffs.

### Required Clarifications Before Approval
1. Does "machine appears in each room" mean after every combat room clear: rooms 1, 2, 3, 4, and 5?
2. Does every machine stop grant exactly 1 buff card, even if the player lacks tokens?
3. If tokens still matter, what happens when the player cannot pay: no buff, free minor buff, or delayed spin?
4. With 5 machine stops instead of 3, what are the standard spin costs per stop?
5. Does the optional cursed deal remain only on the second machine stop?
6. Should the acceptance criteria say the player can receive up to 5 standard buffs per run?

### BA Decision
Do not route to [[Architect]] yet. Route back to [[GameDesigner]] for a focused casino-machine cadence and buff-flow revision.

## BA Pet Removal - 2026-05-13
**Validation status: BLOCKED.** The human owner requested removal of the pet/helper from the GDD.

### Applied Scope Change
- The active MVP no longer includes a pet/helper companion system.
- The active MVP no longer includes `Pisary`, helper attacks, helper token pickup, helper upgrades, helper SFX, helper reward category, helper loadout, or helper command behavior.
- The 3 helper reward cards were removed from the active `MVP reward pool`, reducing the active standard pool from 15 cards to 12 cards.

### Remaining Design Work
GameDesigner must account for this while fixing machine cadence:
- Decide whether the MVP should stay at 12 standard buff cards or replace the 3 removed helper cards with non-pet buffs.
- Update machine cadence and buff-flow math after both changes: machine every room and no helper rewards.
- Ensure no active MVP section reintroduces pet/helper behavior.

### BA Decision
Do not route to [[Architect]] yet. Continue with `Tasks/Open/10-revise-gdd-machine-each-room.md`, now expanded to include pet/helper removal cleanup.

## GameDesigner Machine Cadence Revision - 2026-05-13
**Revision status: READY FOR [[BA]] re-validation.** The MVP machine cadence has been rewritten around the owner's automatic room-clear reward direction.

### Locked Changes
- MVP run structure is exactly 5 combat rooms, 5 automatic post-combat machine stops, and 1 boss.
- The Sacred Demon Machine appears automatically after every cleared combat room: rooms 1, 2, 3, 4, and 5.
- The player does not walk to the machine and does not press a manual spin button; the machine auto-rolls with a 0.8-1.2 second animation.
- Each machine stop shows 3 readable standard buff cards and requires the player to choose exactly 1.
- Standard room-clear buffs are guaranteed and free; tokens do not gate normal buffs in MVP.
- The player starts with 3 total reroll charges per run. Reroll replaces all 3 visible standard cards, spends 1 charge, and charges do not refresh during the run.
- Selected standard cards never appear again in the same run, and duplicate standard cards never appear inside one 3-card offer.
- The optional cursed deal remains only on machine stop 2 and is not changed by rerolling normal cards.
- The active MVP reward pool remains 12 standard cards after pet/helper removal. No active MVP section requires Писарь, helper commands, helper pickups, helper attacks, helper reward cards, or helper SFX.

### Self-check Before BA
- Movement-only portrait combat is preserved: one floating joystick, no dash button, no possession button, no helper command button, auto-attack always on, and automatic marked-vessel possession.
- The old 3-machine cadence is removed from active GDD sections: core loop, run structure, machine section, systems table, in-run progression, MVP scope, acceptance criteria, and 10 MVP decisions.
- Tokens are now a pickup/score currency for MVP, not the cost of standard machine rewards or rerolls.

### BA Handoff Note
BA should re-check the machine flow, reroll rules, cursed deal isolation, 12-card reward pool, no-pet cleanup, and movement-only combat acceptance criteria before routing to [[Architect]].

## BA Machine Cadence Re-validation - 2026-05-13
**Validation status: BLOCKED.** The machine cadence and no-pet cleanup are implementation-ready, but the possession-explosion behavior needs one explicit owner-aligned decision before [[Architect]] routing.

### Passes
- MVP run structure is now consistent: 5 combat rooms, 5 automatic post-combat machine stops, and 1 boss.
- The Sacred Demon Machine appears after every cleared combat room, rooms 1-5, and never during active combat.
- The machine auto-rolls without manual walk-up or manual spin input.
- Each machine stop shows 3 readable standard buff cards and grants exactly 1 selected standard buff.
- Standard room-clear buffs are free and guaranteed; tokens do not block normal MVP buffs.
- The player starts with 3 total reroll charges; reroll replaces all 3 visible standard cards and charges do not refresh.
- Selected standard cards do not reappear in the same run, and duplicate standard cards do not appear in one offer.
- The optional cursed deal remains only on machine stop 2 and is not changed by normal-card reroll.
- The active MVP reward pool contains exactly 12 standard cards and no pet/helper reward category.
- Active MVP scope still uses movement-only portrait combat: one floating joystick, no dash button, no possession button, no helper command button, auto-attack always on, and automatic marked-vessel possession.

### Blocking Issue
The current GDD does **not** make a marked possessed enemy automatically explode by default. Active rules say basic possession destroys the vessel on exit, while explosion is available only through the standard buff **P03 Последний вздох**:
- Possession section: basic possession destroys the vessel; explosion effects are available only through specific upgrades.
- Reward pool: **P03 Последний вздох** makes the target explode after exiting possession.

If the owner expects the marked enemy to automatically explode after possession, the GDD must say so directly in the possession section, MVP scope, and acceptance criteria. If explosion should remain an optional buff, the GDD must explicitly confirm: "Default marked-vessel possession does not explode; only P03 causes an exit explosion."

### Required Clarification Before Approval
1. Should every marked-vessel possession automatically explode on exit in MVP?
2. If yes, what triggers the explosion: timer end, room clear, controlled enemy death, manual-less exit, or all possession exits?
3. If yes, what is the exact explosion radius and damage, and does it damage the hero body?
4. If yes, should **P03 Последний вздох** be removed or redesigned because the default behavior already explodes?
5. If no, add an explicit acceptance criterion that default marked-vessel possession does not explode and only **P03 Последний вздох** adds the explosion.

### BA Decision
Do not route to [[Architect]] yet. Route back to [[GameDesigner]] for a focused possession-explosion clarification.

## GameDesigner Possession-Explosion Clarification - 2026-05-14
**Revision status: READY FOR [[BA]] re-validation.** The possession-explosion blocker is resolved with a buff-only MVP rule.

### Locked Decision
- Default marked-vessel possession does **not** automatically explode after possession.
- Basic possession exit destroys the vessel without extra token, pickup, explosion VFX, or area damage.
- **P03 Последний вздох** is the only MVP source of possession-exit explosion.

### P03 Implementation Rule
- **P03 Последний вздох** triggers on any possession exit: timer end, room clear, or controlled-enemy death.
- The explosion spawns at the destroyed vessel position.
- It deals 2 damage to living enemy units within 2 gameplay meters.
- It does not damage the hero body.
- It creates no extra token or pickup.
- It uses 1 active VFX slot; if the 12-VFX cap is full, damage still applies but no new visual effect is spawned.

### BA Handoff Note
BA should verify the active possession rules, MVP scope, MVP acceptance criteria, and P03 reward row now all answer the same question: marked-vessel possession does not explode by default; only **P03 Последний вздох** adds the exit explosion.

## BA Possession-Explosion Re-validation - 2026-05-14
**Validation status: APPROVED as validated requirements.** The possession-explosion clarification is logically consistent and ready for [[UXDesigner]] routing under the 8-agent pipeline.

### Confirmed
- Active possession rules explicitly state that marked-vessel possession does not explode by default.
- Default possession exit destroys the vessel without explosion VFX, area damage, extra token, or pickup.
- **P03 Последний вздох** is the only MVP source of possession-exit explosion.
- **P03 Последний вздох** defines all required implementation details: trigger timing, damage, radius, target filter, hero-body damage rule, token/pickup rule, and VFX-cap behavior.
- MVP scope and MVP acceptance criteria match the buff-only explosion decision.
- The active MVP reward pool remains exactly 12 standard cards, and **P03 Последний вздох** remains uniquely useful.
- No active MVP section reintroduces a pet/helper system, dash button, manual possession button, or manual machine spin.

### BA Decision
No blocking ambiguity remains in the active MVP GDD. Route [[GDD]] to [[UXDesigner]] for mobile portrait UX/UI specs before [[Architect]] implementation task breakdown.
