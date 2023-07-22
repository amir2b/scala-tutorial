# Match

```scala
object Main extends App {
  println(finder(1))
  println(finder(1.2))
  println(finder(true))
  println(finder('A'))
  println(finder("Amir"))

  def finder(in: Any): String = {
    in match {
      case number: Int => s"$number is integer"
      case number: Double => s"$number is decimal"
      case bool: Boolean => s"$bool is boolean"
      case chr: Char => s"$chr is character"
      case str: String => s"$str is string"
      case _ => "Other types"
    }
  }
}
```

# Pattern guards

Pattern guards are boolean expressions which are used to make cases more specific. Just add `if <boolean expression>` after the pattern.

```scala
import scala.util.Random

object Main extends App {
  Random.nextInt(30) match {
    case x if x < 10 => println(s"0 <= $x < 10")
    case x if 10 < x && x < 20 => println(s"10 <= $x < 20")
    case x => println(s"20 <= $x")
  }
}
```

## References

* https://docs.scala-lang.org/tour/pattern-matching.html
