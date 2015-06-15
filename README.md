Enum-Oriented Programming
========

This is a an adaption of Apple’s sample code for the [Protocol-Oriented Programming in Swift](https://developer.apple.com/videos/wwdc/2015/?id=408) talk given during WWDC 2015.

Included is Apple’s original example playground file `Crustacean.playground` and an alternative version `CrustaceanEnumOriented.playground` that uses a recursive enum as the data structure.

The playgrounds demonstrate two different approaches to creating `Diagram`s as value types and show how to draw them into a CGContext.

* * *

Apple’s version uses a variety of structs that conform to the `Drawable` protocol to represent different shapes. The alternative approach uses a recursive enum to achieve the same result. It looks like this:

```swift
enum Diagram {
  case Polygon(corners: [CGPoint])
  case Circle(center: CGPoint, radius: CGFloat)
  case Rectangle(bounds: CGRect)
  case Scale(x: CGFloat, y: CGFloat, diagram: Box<Diagram>)
  case Translate(x: CGFloat, y: CGFloat, diagram: Box<Diagram>)
  case Diagrams(diagrams: Box<[Diagram]>)
}
```

Recursive enums still require the use of `Box` in Swift 2.0, but Apple have indicated that they plan to fix this (hopefully soon).
