What is Type Narrowing in TypeScript? Provide practical examples using typeof, instanceof, and the in operator.

Introduction
Type Narrowing a process of finding a specific type from the vast types in typescript. It refines the type of a variable in a conditional block based on runtime checks. It enables more precise typing for avoiding type errors in code execution. It is achived by technics using typeof guards, instance checks or property existence checks.

How Type Narrowing works
1.	Typeof type guards
Typeof guards use typeof to differentiate between two different types for example 

function myFunction(value: string | number) {
    if (typeof value === 'string') {
    
        // Value is treated as string here
        console.log(value.toUpperCase());
    } else {
    
        // Value is treated as number here
        console.log(value.toFixed(2));
    }
}
myFunction("GeeksforGeeks");
myFunction(3.14159);

Reference: geeks for geeks

2. Instaceof type
The instanceof operator checks whether an object was created from a particular class before which is very helpful in error handling. 
for example

function errorMessage(value: unknown): string {
  if (value instanceof Error) {
    return value.message;
  }
  return "Unknown error";
}

3. In operator
The in operator checks whether the property exists in the object it is helpful when different objects have different properties
for example

type Admin = { permissions: string[] };
type Guest = { visitId: number };

function describeUser(user: Admin | Guest): string {
  if ("permissions" in user) {
    return `Admin: ${user.permissions.length} permissions`;
  }
  return `Guest visit: ${user.visitId}`;
}


Conclusion

Type narrowing do not change the runtime type it helps type script to understand what checks have proved. Using them reduces the chances of unsafe assumptions and prevent basic programming mistakes.


