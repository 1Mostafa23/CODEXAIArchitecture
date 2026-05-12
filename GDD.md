# Game Design Document — Евангелие Джекпота

> Written by: [[GameDesigner]]
> Validation: Pending [[BA]] re-check after GameDesigner cleanup on 2026-05-12
> Last updated: 2026-05-12

---

## Elevator Pitch
**Евангелие Джекпота** — это mobile-first roguelite в портретной ориентации, где посланник Хранителей Вселенной очищает зараженный культом мир, вселяется во врагов и покупает случайные благословения у демонического автомата-казино, который сам является святыней врага.

### Рабочая фантазия игрока
Игрок чувствует себя не героем-пророком, а санитаром сломанной веры: он забирает у культа его же инструменты, превращает фанатиков, проповеди, проклятия и игровые автоматы против демона, но постепенно понимает, что Хранители Вселенной тоже не невинны.

### Центральная дизайнерская ставка
Игра должна держаться на трех узнаваемых опорах:
- **Демонический автомат-казино** как основной источник улучшений, риска, юмора и лора.
- **Временное вселение во врагов** как активная тактическая кнопка, меняющая стиль боя на короткое время.
- **Помощник-осколок Хранителя** как эмоциональная и механическая опора, которую можно мутировать через автомат.

### Выбор боевой модели
Рассматривались варианты:
- **Twin-stick shooter**: дает высокий контроль, но требует двух пальцев, загружает экран и хуже подходит для одной руки.
- **Комнатный roguelike как The Binding of Isaac**: хорошо работает для синергий и боссов, но на телефоне может быть медленнее и требовать много навигации.
- **Арена с волнами и auto-attack**: лучше всего читается на мобильном, быстро запускается, поддерживает короткие сессии.

**Основной выбор: гибрид компактных арен-комнат с auto-attack, ручным движением/уклонением и одной активной кнопкой вселения.** MVP использует двухпальцевое портретное управление: левый палец двигает героя, правый палец нажимает рывок и вселение. Auto-attack всегда выбирает ближайшего живого врага в радиусе атаки; при равной дистанции выбирается враг с меньшим текущим HP.

### Краткий elevator pitch для питча
Портретный roguelite про охоту на культ демона-лотереи: уклоняйся, вселяйся во врагов и крути проклятый автомат, чтобы собрать безумный билд до босса.

---

## Core Loop
1. Игрок входит в короткую арену-комнату.
2. Двигается и уклоняется вручную; герой и помощник атакуют автоматически.
3. Убивает врагов, собирает **индульгенционные жетоны** и заряжает шкалу вселения.
4. Временно вселяется во врагов с HP 40% или ниже, чтобы использовать их способности против волны.
5. После 2-й и 4-й боевой комнаты, а также перед боссом, появляется **Священный Автомат Демона**.
6. Игрок платит жетоны, запускает автомат и выбирает 1 из 3 видимых наград: атаку, защиту, мобильность, модификатор вселения или апгрейд помощника.
7. На втором автомате игрок может вместо обычного спина взять 1 явно отмеченную проклятую сделку: сильная награда плюс 1 видимое проклятие.
8. После 5 боевых комнат игрок выходит на босса зоны.
9. После смерти сохраняется только найденный лор текущего забега; после победы над MVP-боссом открывается стартовый знак **Сломанная Печать** для следующих забегов.
10. Игрок начинает следующий забег с новым знанием, а после первой победы — с одним новым стартовым знаком.

### Core loop в одну строку
**Зачисти комнату, собери жетоны, вселись в самого выгодного врага, крути демонический автомат, переживи проклятие и дойди до босса.**

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
- Input: two-thumb portrait controls: left virtual joystick for movement, right-side buttons for dash and possession. Slot-machine interaction happens only after combat stops.
- Frame rate target: 60 fps.
- Session length: MVP run target is 7 minutes from spawn to boss result; acceptable range is 6-8 minutes.

### Управление
- Левая нижняя зона: плавающий виртуальный стик движения.
- Правая нижняя зона: кнопка рывка с cooldown 3 секунды.
- Правая средняя зона: кнопка вселения, активна только при полном заряде и доступной цели.
- Помощник в MVP полностью автоматический; отдельной кнопки команды помощнику нет.
- Auto-attack включен постоянно. Базовая атака срабатывает каждые 0,75 секунды и выбирает ближайшего живого врага в радиусе 6 игровых метров. Если две цели на одинаковой дистанции, выбирается цель с меньшим текущим HP. Если целей в радиусе нет, герой не атакует.

### Вселение во врагов
- Заряд вселения копится только за убийства: обычный враг дает 25%, дальнобойный проповедник дает 35%, боссовые призывы дают 0%.
- Враг становится целью вселения только при HP 40% или ниже.
- Активация: нажать кнопку вселения, когда полный заряд накоплен и в радиусе 4 игровых метров есть подсвеченная цель. Если целей несколько, выбирается ближайшая к герою; при равной дистанции выбирается цель с меньшим HP.
- Базовая длительность: 6 секунд.
- Ограничение: после выхода из врага есть cooldown 10 секунд.
- Тело героя во время вселения остается на месте как пустая оболочка с 60% сопротивления урону.
- Если оболочка уничтожена, забег заканчивается, даже если игрок сейчас внутри врага.
- Если цель умерла до начала вселения, заряд не тратится и способность не активируется.
- Если таймер закончился, комната очищена, или контролируемый враг умер, герой возвращается в оболочку, а цель получает 60 урона и оглушается на 1 секунду.
- Базовое вселение не взрывает врага и не превращает его в союзника; такие эффекты доступны только через конкретные улучшения.

### Типы вселения
| Scope | Тип врага | Способность при вселении | Стратегическая роль |
|---|---|---|---|
| MVP | Слабый культист | Быстрая серия ножевых ударов | Добить плотную группу, дешево и безопасно |
| MVP | Быстрый фанатик | Рывок сквозь врагов | Побег из окружения, сбор жетонов |
| Post-MVP | Святой воин | Щит и таран | Пережить опасную фазу, прорвать броню |
| Post-MVP | Проповедник | Конусная волна лозунгов | Контроль толпы на расстоянии |
| Post-MVP | Мутировавший прихожанин | Взрывная кислотная аура | Рискованный burst-урон |
| Post-MVP | Демонический автомат | Случайный выстрел-символ | Высокий риск, шанс редкого эффекта |
| Post-MVP | Элитный сосуд | Уникальная мини-способность | Самая выгодная цель, требует подготовки |

### Mobile readability
- Не больше 10 обычных врагов одновременно в MVP; элитные враги не появляются в MVP.
- Не больше 18 вражеских снарядов одновременно в MVP.
- Не больше 30 видимых подбираемых жетонов одновременно в MVP; лишние жетоны объединяются в один pickup с суммарным значением.
- Не больше 12 активных VFX-объектов одновременно в MVP, включая взрывы, следы рывка, попадания и эффекты проклятий.
- Враги читаются силуэтом: маленькие, быстрые, бронированные, дальнобойные, элитные.
- Улучшения показываются крупными карточками по 3 варианта, без мелкого текста в бою.
- Цвета эффектов закреплены по категориям: атака — красный, защита — синий, мобильность — желтый, вселение — фиолетовый, помощник — зеленый, проклятие — черный/белый.
- Все боевые кнопки находятся справа и рассчитаны на правый большой палец; минимальный размер интерактивной кнопки — 72x72 px на эталонном 1080x1920 экране.

---

## Scenes
| Scene | Purpose |
|-------|---------|
| MainMenu | Start button, текущая зона, выбранный помощник, базовые разблокировки, доступ к лору |
| Game | Core gameplay loop: арены, волны, жетоны, вселение, помощник, автомат, босс |
| GameOver | Итог забега, найденные фрагменты, причина смерти, быстрый restart, переход в меню |

### Дополнительные экраны после MVP
| Scene | Purpose |
|---|---|
| Loadout | Выбор стартового помощника, стартового знака Хранителей и косметики |
| LoreArchive | Фрагменты о Хранителях, Азартале и происхождении автомата |
| ShopCosmetic | Только косметика, визуальные темы и отключение рекламы; без продажи силы |
| ZoneMap | Легкая карта прогресса по зонам, без сложной навигации |

### Структура одного забега
- 5 боевых комнат по 45-60 секунд каждая.
- Автомат после комнаты 2.
- Автомат после комнаты 4.
- Предбоссовый автомат после комнаты 5.
- 1 босс на 90-120 секунд.

Для MVP используется одна зона: "Приход Первого Спина". В MVP нет карты маршрута, элитных комнат, событий, специальных святынь и автомата внутри активного боя.

---

## Systems
| System | Description | Priority |
|--------|-------------|----------|
| Player movement and auto-combat | Портретное движение, auto-attack, рывок, здоровье, получение урона | MVP |
| Arena wave director | Компактные комнаты, волны врагов, выход после зачистки | MVP |
| Demonic slot machine | Жетоны, 3 фиксированных появления, выбор 1 из 3 наград, 1 опциональная проклятая сделка | MVP |
| Possession | Заряд, выбор цели, временный контроль врага, пустая оболочка героя | MVP |
| Helper companion | Один автоматический помощник-осколок с атакой, сбором жетонов и 3 апгрейдами | MVP |
| Boss encounter | Один босс зоны с двумя фазами и наградой | MVP |
| Run results | Смерть/победа, найденный лор, быстрый restart | MVP |
| Simple meta unlock | После первой победы открывается стартовый знак "Сломанная Печать" | MVP |
| Expanded meta progression | Новые автоматы, помощники, стартовые знаки, косметика | Post-MVP |
| Full biome chain | 4-6 зон с уникальными врагами и боссами | Post-MVP |
| Ethical monetization | Косметика, battle pass без силы, rewarded ads без влияния на баланс | Post-MVP |

### Демонический автомат-казино
Автомат называется **Священный Автомат Демона**. Для культа это алтарь, исповедальня и лотерея спасения. Для героя это украденный инструмент, который перераспределяет силу верующих против них.

#### Валюта
- **Индульгенционные жетоны**: единственная MVP-валюта. Обычный враг имеет 35% шанс уронить 1 жетон, дальнобойный проповедник всегда роняет 1 жетон, босс роняет 5 жетонов только для итогового экрана.
- **Заряд вселения**: отдельная боевая шкала, не валюта и не тратится в автомате.
- **Души сдачи** и **Кредит веры** переносятся в Post-MVP.

#### Где появляется автомат
- В MVP автомат появляется строго 3 раза: после комнаты 2, после комнаты 4, после комнаты 5 перед боссом.
- Автомат появляется только после полной зачистки комнаты, когда враги и вражеские снаряды исчезли.
- Стоимость стандартного спина: 8 жетонов на первом автомате, 10 жетонов на втором, 12 жетонов на предбоссовом.
- Если у игрока не хватает жетонов, стандартный спин недоступен, и игрок может бесплатно взять утешительную награду **Мелкая милость**: лечение 1 HP без выбора улучшения.

#### Типы выпадений
| Категория | MVP-награды | Роль |
|---|---|---|
| Атака | 4 карты: Святая отдача, Кадило очереди, Ритм барабана, Острый купон | Ускоряет зачистку |
| Защита | 3 карты: Печать возврата, Запасной нимб, Милость кассира | Стабилизирует забег |
| Мобильность | 2 карты: Паломнический рывок, Скидка на бегство | Помогает выживать |
| Помощник | 3 карты: Маленький апостол, Ручной сборщик, Служебная печать | Развивает companion build |
| Вселение | 3 карты: Душа напрокат, Нотариальная одержимость, Последний вздох | Делает ключевую механику глубже |
| Проклятая сделка | 1 фиксированная сделка на втором автомате: Фанатичный кредит | Создает контролируемый риск |

#### Риск и честность
- Стандартный спин всегда показывает 3 видимые карты наград, и игрок выбирает 1.
- Карты выбираются случайно из 15 стандартных MVP-наград без дублей внутри одного показа; уже выбранные в этом забеге карты повторно не появляются.
- Стандартный спин никогда не выдает проклятие.
- На втором автомате дополнительно появляется одна кнопка **Проклятая сделка**. Она бесплатна, требует отдельного подтверждения и показывает точную пару: награда + проклятие.
- Единственная MVP-проклятая сделка — **Фанатичный кредит**: немедленно получить **Острый купон** (+1 урон базовой атаки), но все последующие стандартные спины в этом забеге стоят на 2 жетона дороже.
- В MVP за забег можно взять максимум 1 проклятие.
- Предбоссовый автомат не предлагает проклятую сделку.
- Реальные деньги никогда не покупают спины, силу, шансы или жетоны.
- Rewarded ads могут дать только косметический reroll внешнего вида награды или небольшую внебоевую валюту после забега, не влияющую на текущий run.

### Помощник
Рассматривались варианты:
- Маленький демон: хорошо подходит тону, но дублирует врага.
- Воскресший культист: смешно и мрачно, но менее связан с Хранителями.
- Осколок Хранителя в механической кукле: связывает космический сюжет, визуально читается и дает простор для мутаций.

**Выбранный вариант: Осколок Хранителя в механической кукле, прозвище "Писарь".**

Писарь — маленькая кривая кукла с печатью вместо лица. Он якобы ведет отчет о миссии, но постоянно ошибается, спорит с автоматами и комментирует абсурд культа. В бою он:
- стреляет слабым снарядом по ближайшему врагу каждые 1,25 секунды;
- собирает жетоны в радиусе 2 игровых метров от героя;
- действует полностью автоматически и не имеет активной кнопки команды в MVP;
- получает только 3 MVP-апгрейда: **Маленький апостол** (второй снаряд), **Ручной сборщик** (+1 метр радиуса сбора), **Служебная печать** (каждые 8 секунд выпускает импульс замедления на 1 секунду).

### Прогрессия внутри забега
- Игрок получает до 3 стандартных наград за забег, по одной с каждого автомата.
- На втором автомате игрок может заменить стандартный спин одной проклятой сделкой.
- Каждая награда принадлежит одной MVP-категории: атака, защита, мобильность, помощник, вселение.
- Помощник получает максимум 2 апгрейда за забег, потому что пул помощника может появиться не на каждом автомате.
- Вселение меняется только через конкретные награды: +1 секунда длительности, взрыв после выхода, временный союзник после выхода.

### Прогрессия между забегами
- До первой победы между забегами сохраняются только открытые фрагменты лора.
- После первой победы над Матушкой Купонеллой открывается один стартовый знак: **Сломанная Печать**.
- **Сломанная Печать** дает +1 начальный индульгенционный жетон при старте нового забега.
- Постоянные стат-бонусы, новые типы автоматов, новые помощники, косметика и дополнительные стартовые знаки переносятся в Post-MVP.

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
| M01 | Мобильность | Паломнический рывок | Рывок оставляет след на 1 секунду; враги в следе замедляются на 30% |
| M02 | Мобильность | Скидка на бегство | Cooldown рывка уменьшается с 3 до 2,5 секунды |
| H01 | Помощник | Маленький апостол | Писарь выпускает второй снаряд при каждой атаке |
| H02 | Помощник | Ручной сборщик | Писарь получает +1 метр к радиусу сбора жетонов |
| H03 | Помощник | Служебная печать | Каждые 8 секунд Писарь выпускает импульс, замедляющий ближайших врагов на 1 секунду |
| P01 | Вселение | Душа напрокат | Длительность вселения увеличивается с 6 до 7 секунд |
| P02 | Вселение | Нотариальная одержимость | После выхода из вселения цель 2 секунды сражается за игрока |
| P03 | Вселение | Последний вздох | После выхода из вселения цель взрывается и наносит 2 урона врагам в радиусе 2 игровых метров |

### MVP cursed deal
| Scope | Сделка | Награда | Проклятие |
|---|---|---|---|
| MVP | Фанатичный кредит | Немедленно получить карту **Острый купон**; если она уже выбрана, получить **Ритм барабана** | Все последующие стандартные спины в этом забеге стоят на 2 жетона дороже |

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
| Post-MVP | Казино-монастырь "Обитель Трех Барабанов" | Монастырские арки, неоновые витражи, барабаны вместо икон | монахи-дилеры, святые воины, автоматы-враги | вращающиеся пола, ловушки-монеты, двери за жетоны | Брат Барабаний | автомат помощника, защитные улучшения |
| Post-MVP | Катакомбы проигравших душ | Кладбище, кассы индульгенций, кости как жетоны | мертвые должники, призраки, проповедники | долговые цепи, могилы-ловушки, налог на лечение | Индульгент Проигравших | проклятые сделки, усиления вселения |
| Post-MVP | Собор демонической лотереи | Огромный собор с лототроном вместо алтаря | проповедники, элитные сосуды, фанатики | падающие шары-номера, зоны "выигрыша" и "штрафа" | Архирекламщик Вельзевит | джекпот-улучшения, редкие синергии |
| Post-MVP | Небесная канцелярия Хранителей | Бело-золотой офис вне мира, печати, очереди душ, сломанные формы | архивариусы, печатники, стражи вероятности | бюрократические барьеры, отмена эффектов, задержка кнопок | Секретарь Ноль-Ноль | стартовые знаки Хранителей, лор |
| Post-MVP | Тронный зал Азартала | Красно-черная капелла с бесконечными автоматами и живыми барабанами | все классы врагов, усиленные автоматы | случайные правила комнаты, проклятые джекпоты | Азартал Святой Шанс | финальный выбор, окончание арки |

### Враги
| Scope | Класс | Поведение | Атаки | Контр-игра | Награда за вселение |
|---|---|---|---|---|---|
| MVP | Слабый культист | Идет группой, давит числом | короткий удар ножом, бросок свечи | держать дистанцию, использовать отталкивание | быстрые удары, безопасное добивание |
| MVP | Быстрый фанатик | Рывками обходит игрока | прыжок, саморазгон | ждать рывок, уходить в сторону | скоростной dash сквозь толпу |
| MVP | Дальнобойный проповедник | Держится краев арены | конус лозунгов, проклятый снаряд | быстро сближаться и уклоняться от конуса | нет вселения в MVP |
| Post-MVP | Бронированный святой воин | Медленно наступает, закрывает других | щитовой таран, удар колоколом | заходить сбоку, использовать взрывы | щит, таран, временная броня |
| Post-MVP | Мутировавший прихожанин | Непредсказуемо меняет форму | плевок воском, кислотная аура | не стоять рядом долго | аура урона и взрыв при выходе |
| Post-MVP | Демонический автомат | Стоит как объект, потом оживает | снаряды-символы, притяжение жетонов | ломать между волнами, избегать линий | случайный символ-выстрел, шанс мини-спина |
| Post-MVP | Элитный сосуд веры | Редкий сильный враг с подсветкой | комбинированные атаки | копить заряд вселения специально под него | уникальная способность комнаты |

### Боссы
| Scope | Босс | Образ и роль | Фазы | Уникальная механика | Награда |
|---|---|---|---|---|---|
| MVP | Матушка Купонелла | Староста деревни, святая промо-акций, лицо закрыто стопкой купонов | 1: призывает культистов; 2: режет арену скидочными лентами | "Акция дня": каждые 20 секунд создает одну опасную красную ленту и одну безопасную золотую зону | сюжетный фрагмент и стартовый знак "Сломанная Печать" |
| Post-MVP | Брат Барабаний | Монах-казначей с тремя барабанами вместо туловища | 1: вращает паттерны снарядов; 2: меняет правила комнаты каждые 10 секунд | Игрок может вселиться в один барабан и остановить паттерн | апгрейд помощника-щита |
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
- SFX: attack hit, dash, possession start/end, token pickup, slot spin, jackpot, curse, helper mutation, boss phase shift.

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

- [ ] One portrait arena zone with exactly 5 combat rooms, 3 post-combat machine stops, 1 boss, and a 6-8 minute playable run.
- [ ] Two-thumb portrait controls: left joystick, right dash button, right possession button.
- [ ] Player movement, deterministic nearest-target auto-attack, 3-second dash, health, damage, death, and restart.
- [ ] Three enemy classes: weak cultist, fast fanatic, ranged preacher.
- [ ] Possession of weak cultist and fast fanatic using the 40% HP trigger, 6-second duration, 10-second cooldown, and empty-body fail rule.
- [ ] Demonic slot machine after rooms 2, 4, and 5 with 15 standard reward cards and 1 optional cursed deal on the second machine.
- [ ] One automatic helper, Писарь, with base attack, token pickup and 3 possible upgrades.
- [ ] One boss, Матушка Купонелла, with two phases.
- [ ] Run results screen with collected tokens, one lore fragment, unlocked start sign status, and quick restart.
- [ ] One concrete meta reward: after first boss victory, unlock **Сломанная Печать** for +1 starting token.

### MVP acceptance criteria
- On a 1080x1920 Android test screen, joystick, dash button, and possession button are visible during combat and each combat button is at least 72x72 px.
- Auto-attack selects the nearest living enemy within 6 gameplay meters; when two enemies are equally distant, the enemy with lower current HP is targeted.
- A full MVP run contains 5 combat rooms, machine stops after rooms 2, 4, and 5, and 1 boss encounter.
- During combat, the game never exceeds 10 enemies, 18 enemy projectiles, 30 visible pickups, or 12 active VFX objects at the same time.
- The first machine stop appears no later than 120 seconds after run start during a normal room clear.
- Standard machine interaction shows 3 readable reward cards and lets the player select exactly 1 card.
- Standard machine cards are drawn from the 15-card `MVP reward pool` without duplicates inside one 3-card offer.
- The second machine stop shows the optional **Фанатичный кредит** cursed deal; accepting it grants **Острый купон** or **Ритм барабана** if **Острый купон** was already selected, adds the +2 future spin cost curse, and disables further cursed deals for the run.
- Possession can be activated only at 100% charge against an enemy at 40% HP or lower within 4 gameplay meters.
- If the hero body reaches 0 HP during possession, the run ends immediately and shows the GameOver screen.
- Писарь fires automatically every 1,25 seconds and collects visible tokens within 2 gameplay meters of the hero.
- After death or victory, the GameOver screen shows a restart button within 3 seconds.
- After the first boss victory, the next run starts with **Сломанная Печать** active and +1 starting token.

### Коммерческое позиционирование
1. **"Vampire Survivors meets cursed slot machines"** — для игроков, которые хотят быстрые мобильные забеги и смешные синергии.
2. **"A dark cult roguelite built for portrait play"** — акцент на мобильность, стиль и короткие сессии.
3. **"Possess enemies, rig the demon's machine, break the gospel of chance"** — акцент на уникальные механики и сюжетный крючок.

### 10 MVP decisions before prototype
1. Auto-attack targets the nearest living enemy within 6 gameplay meters; equal-distance ties target the lower-HP enemy.
2. Combat rooms target 45-60 seconds each; the full MVP run target is 7 minutes with an acceptable 6-8 minute range.
3. Possession requires the target enemy to be at 40% HP or lower; there is no separate "сломленная вера" meter in MVP.
4. The hero body has 60% damage resistance during possession, but death of the body immediately ends the run.
5. A run can contain at most 1 curse: **Фанатичный кредит**, available only on machine stop 2.
6. Standard machine spins always show 3 visible rewards and require the player to choose exactly 1; there is no reroll in MVP.
7. MVP reward categories are attack, defense, mobility, possession, and helper; curses exist only as the cost of the one cursed deal.
8. Писарь is fully automatic in MVP and has no command button.
9. MVP uses two-thumb portrait controls and a 10-enemy simultaneous cap for readability.
10. The first Хранители twist appears after the first boss victory as the unlocked lore fragment tied to **Сломанная Печать**.

## Out of Scope (v1)
- Full 6-zone campaign.
- More than one playable hero.
- One-thumb control mode.
- Complex procedural map with branching routes.
- Full narrative dialogue system.
- More than one helper archetype.
- Manual helper command button.
- Souls, Credit Faith, multiple machine types, rerolls, combat-time machine interaction, elite rooms, and in-run shops.
- Post-MVP enemies, possession types, biomes, bosses, jackpots, and risk-deal cards listed outside the MVP tables.
- Online leaderboards, multiplayer, clans, social systems.
- Real-money power purchases, paid run upgrades, paid slot spins, paid odds boosts.
- Aggressive ads, forced ads inside a run, gambling monetization.
- Battle pass implementation.
- Advanced analytics and live ops balancing.
- Localization beyond the working design language.

### Этичная монетизация после MVP
- Косметические облики героя, Писаря, автоматов и жетонов.
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
