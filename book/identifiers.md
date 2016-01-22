# Identifiers
An identifier is a sequence of Unicode code points encoded in UTF-8. An
identifier can consist of letters, digits, or underscores. However, the
identifeir **must** begin with either a letter, or an underscore.

    func 1something...          // INVALID!
    func _something...          // VALID
    func __something...         // VALID
    func 21something...         // INVALID!
    func foo_bar...             // VALID
    func __some_123123_th...    // VALID

UTF-8 Letters are _allowed_, this means that the following identifier is
valid:

    func 日本語てすと() => do_stuff(1, 2);

And can be called like so:

    日本語てすと();
