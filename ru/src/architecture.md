# Архитектура

Kotlin - это объектно-ориентированный язык, что означает, что обычные данные и методы группируются вместе в классах, и очень редко встречаются методы вне классов, хотя Kotlin без проблем поддерживает это. Кроме того, классы могут расширять друг друга, поэтому многие фреймворки (такие как Android или AWT) в значительной степени полагаются на наследование для обеспечения функциональности классов.

Rust - это язык, ориентированный на данные, программы которого будут больше напоминать программы на C, где программа может быть составлена из нескольких методов и нескольких структур без каких-либо последствий. И поскольку наследование реализации в Rust невозможно, а наследование типажей на самом деле не приносит особой пользы, часто используется композиция.

Тем не менее группировка логики и данных по-прежнему в порядке и выполнены с помощью Rust:

```kotlin
class Point(
	val x: Float,
	val y: Float
){
	fun distanceTo(other: Point): Float {...}
	fun angleTo(other: Point): Float {...}
}
```

может выглядеть как:

```rust,ignore
struct Point {
	x: f32,
	y: f32
}

impl Point {
	fn new(x: f32, y: f32) -> Point {
		return Point {x, y};
	}
}

impl Point {
	fn distance_to(other: Point) -> f32 {...}
	fn angle_to(other: Point) -> f32 {...}
}
```