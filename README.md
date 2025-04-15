# theCuriousCaseOfNullsType

There's a strange quirk when you check the type of null in JavaScript.

const whatIsTheTypeOfNull = typeof null;

// Result: object

Wait, what?

Upon first glance, it's an unusual output. Why would null be of type object? Isn't it a primitive? Similar to how undefined is typeof undefined?

Thinking back to JavaScript 101 days, it could be a fairly easy to reason that, well, it must be because primitive values often get wrapped in an object wrapper when accessed. Similar to how string is a primitive type, but there are a whole host of string properties and methods on it. (Which also explains how a string is immutable, but seemingly mutable via the object (Technically its entirely replaced in memory when its "changed"))

Except the funny thing here is that null has exactly 0 properties or methods. There's nothing to access on it at all. It can only be used for its reference, and reading it's stored type.

So we're back to the drawing board— why in the world would null be of type object?

Well, it turns out, to no one's surprise at all, that the answer is... :drum_with_drumsticks:
                               ...Null is of type object because of a legacy bug from 1995! :tada:
                               
The behavior originated from the way early JavaScript engines represented types internally using type tags—specifically, a few bits in memory to indicate a value's type. Both object and null were accidentally assigned the same tag (000), causing typeof null to incorrectly return object. Despite being recognized as a bug, it was never fixed because millions of websites and libraries relied, and still rely, on this behavior. Changing it now would break backward compatibility across the web. So it is a quirk that will remain preserved for legacy reasons.
