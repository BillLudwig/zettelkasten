title:: CSharp v11
tags:: Dev, .NET, CSharp

-
- ## List<T> Performance
	- [Performance gains when specifying a List’s capacity Part 1](https://intodot.net/performance-gains-when-specifying-a-lists-capacity/) [Part 2](https://intodot.net/performance-gains-when-specifying-a-lists-capacity-part-2/)
		- The capacity [property](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.capacity?view=net-6.0) "Gets or sets the total number of elements the internal data structure can hold without resizing."
		- Without an initial capacity it is set to `0` by default, then grows to 4, then doubles as items are added.
		- The number of times this happens can be reduced or eliminated by setting a capacity, making it faster.
- ## Sealed Class Performance
	- [Boosting Performance with sealed classes](https://code-maze.com/improve-performance-sealed-classes-dotnet/) by Marko Hrnčić
		- **This will cause problems with testing with mocks because mocking sealed classes doesn't work**
		- Sealed classes are faster in all cases except when calling a static method from parent class
		- "When we call overridden methods in sealed classes, this is done **directly on the memory address of the sealed class object**. In an open class, we need to call methods through virtual dispatch. **The virtual dispatch cannot use a direct call **since it has to check if the method has been overridden."
- ## Raw String Literals
	- Now instead of having just [string interpolation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated) with the `$` syntax and [verbatim](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/verbatim) with the `@` syntax we now also have [string literals](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-11.0/raw-string-literal) with the `"""` syntax.
		- String literals don't need to have escapes around quotes and automatically trim leading and following white space.
		- They can be mixed for extra fun.
			- `var location = $$""" You are at {{{Longitude}}, {{Latitude}}}  """;`
- ## List Pattern Matching with discard `_` and Range `...`
	- Using the [discard _](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/discards) and [range ...]() patterns is now allowed for [list patterns](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching#list-patterns).
	- [Introducing C#11: List Pattern](https://anthonygiretti.com/2022/11/29/introducing-c11-list-pattern/)
- ## Required Properties
	- You can now mark a property as `required` and it will throw an error if it is now initialized in the constructor.
		- `public required string Property { get; set; }`