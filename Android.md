1. Difference between onStart() and onCreate()
2. Describe thereading.
3. Describe the scenario where polymorphism is implemented.
4. Types of service
5. What's the role of IO Thread and MAIN thread.
6. How does ViewModel work under the hood.
7. How does Recyclerview work under the hood.
8. Role of scoping of viewmodel.
9. What's AIDL , what the replacement of it.
10. How to get the result from a IO thread to a MAIN Thread ?
11. How are andoird apps signed.
12. What's memory leak, how does it happens, how to avoid it.
13. Serialize vs Percalize diffrence.
14. Types of Intents.
15. What are IPC's ?
16. What are data classes why are they used.
17. How does navigation in android work?
18. Briefly describe about notification.
19. viewModelScope.launch vs coroutineScope.launch vs withcontext

viewModelScope.launch
Scope: Tied to the lifecycle of a ViewModel.
Dispatcher: Implicitly uses Dispatchers.Main.
Cancellation: Automatically cancels coroutines when the ViewModel is cleared.   
Purpose: Ideal for UI-related work that needs to be executed on the main thread and should be tied to the ViewModel's lifecycle.   

coroutineScope.launch
Scope: Defined by the caller. Can be a custom scope or a built-in one like GlobalScope (not recommended).
Dispatcher: Requires explicitly specifying a dispatcher.
Cancellation: Depends on the parent scope's cancellation.
Purpose: Flexible for various use cases, but requires careful management of the scope and dispatcher to avoid potential issues.

withContext
Purpose: Switches the context of a coroutine for a specific block of code.
Dispatcher: Requires explicitly specifying a dispatcher.
Cancellation: Inherits cancellation from the parent coroutine.
Purpose: Used to perform tasks on a different thread without creating a new coroutine.

21. How do you create a new Coroutine .

Coroutines are lightweight threads managed by the Kotlin coroutines library. To create a new coroutine, you typically use a coroutine builder within a coroutine scope.   

Coroutine Builders
These are functions that create new coroutines. The most common ones are:   

launch: Creates a "fire and forget" coroutine that doesn't return a value.   
async: Creates a coroutine that computes a result and returns a Deferred object, which can be used to obtain the result later.
Coroutine Scope
A coroutine scope defines the lifecycle of a coroutine. When a coroutine scope is canceled, all coroutines launched within it are also canceled. Common scopes include:   

GlobalScope: Avoid using this as it can lead to memory leaks.   
viewModelScope: For UI-related work tied to the ViewModel's lifecycle.   
lifecycleScope: For coroutines tied to an Android Lifecycle component.   
CoroutineScope: Create a custom scope using CoroutineScope(CoroutineName("MyScope")).
