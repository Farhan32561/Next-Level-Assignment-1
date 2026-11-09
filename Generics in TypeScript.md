How do Generics work in TypeScript, and how do they help when working with asynchronous Promise<T> responses?

Introduction 
Generics lets us write reusable typescript code avoiding the unsafe any type by using type parameter such as T to specify the type in a argument. Without creating seperate functions for strings,numbers or objects we can specify them with T.

Reusing Fucntions with generics:

function firstItem<T>(items: T[]): T | undefined {
  return items[0];
}

const firstNumber = firstItem([10, 20]);
const firstName = firstItem(["Rina", "Hasan"]);

here T becomes a number in the first call and string in the second. The undefined return type is important because of the empty array has no first element. The generics runs the function while preserving useful type checking.

Generics with Asynchronous Operations

A Promise<T> describes a value that may become available later. The T represents the type of the value produced when the Promise resolves. We can combine a generic function with a Promise like this:


async function delayedValue<T>(value: T): Promise<T> {
  return new Promise<T>((resolve) => {
    setTimeout(() => resolve(value), 1000);
  });
}

const numberResult: Promise<number> = delayedValue(42);
const textResult: Promise<string> = delayedValue("Done");

Both calls reuse the same logic but keep different result types. When we use await, TypeScript understands whether the resolved value is a number or a string. This idea is also helpful when designing functions for API responses, although external JSON still needs runtime validation.


Conclusion

Generics Makes program reusable and easier to maintain and refactor. With promise<T> they give asynchronous code predictable and clearly type result without sacrificing flexibility.