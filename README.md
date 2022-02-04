#Programación Orientada a Objetos con TypeScript

## Iniciando un proyecto TypeScript
``` shell
  npm init --yes
  npm i -D typescript ts-node
```
## Ejecución de ts-node
En la termnal ejecuta el siguiente comando
``` shell
  npx ts-node index.ts
```
## Variables con tipos de dato
``` typescript
  let message: string;
  message = 'pato';

  let number: number;
  number = 1.45;

  let is: boolean = true;
```
## Funciones con tipos de dato
``` typescript
  function sum(a: number, b: number): number {
    return a + b;
  }

  const result: number = sum(2, 5);
  console.log(result);
```
## Clases y Objetos
``` typescript
  class Sale {
    amount:number;

    getTotal(): number {
      return this.amount;
    }
  }

  const sale = new Sale();
  sale.amount = 10;
  const res = sale.getTotal();
  console.log(res);
```
## Constructores
``` typescript
  class Sale {
    amount:number;

    // Constructors
    constructor(amount: number) {
      this.amount = amount;
    }

    getTotal(): number {
      return this.amount;
    }
  }

  const sale = new Sale(20);
  sale.amount = 10;
  const res = sale.getTotal();
  console.log(res);
```

## Modificadores de acceso
``` typescript
  class Sale {
    // Access modifiers
    protected amount: number;

    constructor(amount: number) {
      this.amount = amount;
    }

    getTotal(): number {
      return this.amount;
    }
  }

  const sale = new Sale(20);
  const res = sale.getTotal();
  console.log(res);
```
## Herencia
``` typescript
  class Sale {
    protected amount: number;

    constructor(amount: number) {
      this.amount = amount;
    }

    getTotal(): number {
      return this.amount;
    }
  }

  // Inheritance
  class SaleWithTaxes extends Sale {
    private tax: number;

    constructor(tax: number, amount: number) {
      super(amount);
      this.tax = tax;
    }

    getTotal(): number {
      return this.tax + super.getTotal();
    }
  }

  const saleWithTaxes = new SaleWithTaxes(16, 100);
  const res2 = saleWithTaxes.getTotal();
  console.log(res2);
```
## Sobreescritura de métodos
``` typescript
  class Sale {
    protected amount: number;

    constructor(amount: number) {
      this.amount = amount;
    }

    getTotal(): number {
      return this.amount;
    }
  }

  // Inheritance
  class SaleWithTaxes extends Sale {
    private tax: number;

    constructor(tax: number, amount: number) {
      super(amount);
      this.tax = tax;
    }

    // method overrides
    override getTotal(): number {
      return this.tax + super.getTotal();
    }
  }

  const saleWithTaxes = new SaleWithTaxes(16, 100);
  const res2 = saleWithTaxes.getTotal();
  console.log(res2);
```

## Types
``` typescript
  type Beer = {
    name: string;
    alcohol: number;
    brand?: string; // ? optional property
  };

  function show(beer: Beer) {
    console.info(`info: ${beer.name} ${beer.alcohol}`);
  }

  const myBeer: Beer = {
    name: 'Corona',
    alcohol: 7,
    brand: 'Modelo', // optional
  };

  myBeer.name = 'Delirium';
  show(myBeer);
```
## Modificador readonly
``` typescript
  type Beer = {
    readonly name: string; // readonly
    alcohol: number;
    brand?: string;
  };

  function show(beer: Beer) {
    console.info(`info: ${beer.name} ${beer.alcohol}`);
  }

  const myBeer: Beer = {
    name: 'Corona',
    alcohol: 7,
    brand: 'Modelo',
  };

  myBeer.name = 'Delirium'; // readonly
  show(myBeer);
```
## Intersección de types
``` typescript
  type Beer = {
    readonly name: string;
    alcohol: number;
    brand?: string;
  };

  type Snack = {
    nameSnack: string;
    price: number;
  };

  // types intersection
  const combo: Beer & Snack = {
    name: 'Corona',
    alcohol: 4.5,
    nameSnack: 'Pastel',
    price: 100,
  };

  console.info(combo);
```
## Interfaces
``` typescript
  interface Drink {
    name: string;
  }

  interface AlcoholicDrink extends Drink {
    alcohol: number;

    showInfo(): string;
  }

  interface MixedDrink {
    ingredients: string[];
  }

  class Wine implements AlcoholicDrink {
    alcohol: number;
    name: string;

    constructor(name: string, alcohol: number) {
      this.name = name;
      this.alcohol = alcohol;
    }

    showInfo(): string {
      return `info: ${this.name} ${this.alcohol}`;
    }
  }

  class Cooktail implements AlcoholicDrink, MixedDrink {
    alcohol: number;
    name: string;
    ingredients: string[];

    constructor(name: string, alcohol: number, ingredients: string[]) {
      this.name = name;
      this.alcohol = alcohol;
      this.ingredients = ingredients;
    }

    showInfo(): string {
      const ingredientsInfo = this.ingredients.reduce(
        (acumulator, element) => acumulator + " " + element + ", ", "");
      return `info: ${this.name} ${this.alcohol} ingredients: ${ingredientsInfo}`;
    }
  }

  const margarita = new Cooktail("Margarita", 12.5, ["tequila","limon","sal","soda","hielo"]);
  const rioja = new Wine("Vino Rioja", 14);
  const malbec = new Wine("Vino Malbec", 16);

  const ad: AlcoholicDrink[] = [
    margarita, rioja, malbec
  ]

  function showDrinks(drinks: AlcoholicDrink[]): void {
    drinks.forEach(e => console.log(e.showInfo()));
  }

  showDrinks(ad);
```
## Accessors
``` typescript 
  class Account {
    private amount: number;
    private commision: number;

    constructor(amount: number, commision: number) {
      this.amount = amount;
      this.commision = commision;
    }

    set setAmount(amount: number) {
      if(amount < 0) 
        amount = 0;
      this.amount = amount
    }

    get total() {
      return this.amount + this.commision;
    }
  }

  const account = new Account(10, 1);
  account.setAmount = 45;
  console.log(account.total);
```
