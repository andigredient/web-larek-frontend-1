# Проектная работа "Веб-ларек"



Архитектура проекта состоит из:
API, модальных окон, корзины, формы, карточек, страниц

Структура проекта:
- src/ — исходные файлы проекта
- src/components/ — папка с JS компонентами
- src/components/base/ — папка с базовым кодом

Важные файлы:
- src/pages/index.html — HTML-файл главной страницы
- src/types/index.ts — файл с типами
- src/index.ts — точка входа приложения
- src/styles/styles.scss — корневой файл стилей
- src/utils/constants.ts — файл с константами
- src/utils/utils.ts — файл с утилитами


API - набор инструментов, которые позволяют взаимодействовать веб-странице с сервером
Модальное окно - окно веб-страницы, которое позволяет блокировать контент, находящийся под ним до тех пор, пока пользователь взаимодействует с окном
Корзина - составная часть веб-страницы, отображающая товары, добавленные в корзину пользователем, и, позволяющая перейти к оформлению заказа через кнопку "Оформить".
Форма - набор полей, кнопок и иных элементов управления, позволяющих получить информацию от поьзователя
Карточки - элемент с текстовым описанием, фотографией и иными элементами, находящийся на странице и позволяющий отобразить модальное окно и добавить выбранный объект в корзину
Страницы - основная часть веб-страницы, содержащая весь контент 

API по запросу выдает объект с категорией, наименованием, фотографией и стоимостью товара, которые отображаются в карточках. Нажав на одну из карточек, открывается модальное окно с развернутым описанием товара и кнопкой с возможностью добавления его в корзину. На модальном окне развернутой карточки отображены фотография, категория, наименование, описание, кнопка с возможностью добавления товара в корзину, стоимость. В корзине отображаются выбранные товары и кнопка с дальнейшим оформлением заказа.



Интерфейс. Описание товара в магазине.
interface ICard {
  id: string;
  title: string;
  description: string;
  image: string;
  category: CategoryType;
  price: number;
  selected: boolean;
}

Тип. Описание категорий товара.
type CategoryType = 'софт-скил' | 'дополнительное' | 'кнопка' | 'хард-скилл' | 'другое';

Интерфейс. Описание корзины товаров.
interface IBasket {
  list: HTMLElement[];
  price: number;
}

Интерфейс. Описание полей формы заказа.
interface IOrder {
  items: string[];
  pay: string;
  total: number;
  address: string;
  email: string;
  phone: string;
}

Интерфейс. Описание полей формы со способом оплаты и адреса доставки
interface IOrder {
  address: string;
  pay: string;
}

Интерфейс. Описание полей формы с Email и телефоном
interface IContacts {
  phone: string;
  email: string;
}

Класс. Описание корзины товара
class Basket extends Component<IBasket> {
  protected _list: HTMLElement;
  protected _price: HTMLElement;
  protected _button: HTMLButtonElement;
  
  constructor(protected blockName: string, container: HTMLElement, protected events: IEvents);

  set price(price: number) {    
  };

  set list(items: HTMLElement[]) {    
  };

  disableButton(): void {    
  };
  update(): void {    
  };
}

Класс. Описание карточки товара
class Card extends Component<ICard> {
  protected _id: HTMLElement;
  protected _title: HTMLElement;
  protected _image: HTMLImageElement;
  protected _category: HTMLElement;
  protected _price: HTMLElement;
  protected _button: HTMLButtonElement;
  
  constructor(protected blockName: string, container: HTMLElement, actions?: ICardActions) {
    };

  set id(value: string) {    
  };

  get id(): string {    
  };

  set title(value: string) {    
  };

  get title(): string {    
  };
 
  set image(value: string) {    
  };

  set category(value: CategoryType) {    
  };
  
  set price(value: number) {    
  };

  set selected(value: boolean) {    
  };
}

Класс. Предназначен для работы с Api
class Api {
    readonly baseUrl: string;
    protected options: RequestInit;

    constructor(baseUrl: string, options: RequestInit = {}) {
    }

    protected handleResponse(response: Response): Promise<object> {        
    }

    get(uri: string) {        
    }

    post(uri: string, data: object, method: ApiPostMethods = 'POST') {        
    }
}

Класс. описание окошка заказа товара
class Order extends Form<IOrder> {
  protected _card: HTMLButtonElement;
  protected _cash: HTMLButtonElement;

  constructor(protected blockName: string, container: HTMLFormElement, protected events: IEvents) {    
  };

  disableButtons(): void {    
  };
}




## Установка и запуск
Для установки и запуска проекта необходимо выполнить команды

```
npm install
npm run start
```

или

```
yarn
yarn start
```
## Сборка

```
npm run build
```

или

```
yarn build
```
