```scala
sealed trait Notification

case class Email(sender: String, title: String, body: String) extends Notification

case class SMS(caller: String, message: String) extends Notification

case class VoiceRecording(contactName: String, link: String) extends Notification
```

`Notification` is a sealed trait which has three concrete Notification types implemented with case classes `Email`, `SMS`, and `VoiceRecording`.

Now we can do pattern matching on these case classes:

```scala
object Main extends App {

  def showNotification(notification: Notification): String = {
    notification match {
      case Email(sender, title, _) =>
        s"You got an email from $sender with title: $title"
      case SMS(number, message) =>
        s"You got an SMS from $number! Message: $message"
      case VoiceRecording(name, link) =>
        s"You received a Voice Recording from $name! Click the link to hear it: $link"
    }
  }

  val someSms = SMS("12345", "Are you there?")
  println(showNotification(someSms))
  // prints: You got an SMS from 12345! Message: Are you there?

  val someVoiceRecording = VoiceRecording("Amir", "https://github.com/amir2b")
  println(showNotification(someVoiceRecording))
  // prints: You received a Voice Recording from Amir! Click the link to hear it: https://github.com/amir2b
}
```

The function `showNotification` takes as a parameter the abstract type `Notification` and matches on the type of `Notification` (i.e. it figures out whether it’s an `Email`, `SMS`, or `VoiceRecording`). In the `case Email(sender, title, _)` the fields `sender` and `title` are used in the return value but the `body` field is ignored with `_`.

## References

* https://docs.scala-lang.org/tour/pattern-matching.html
