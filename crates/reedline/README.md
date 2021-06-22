### Changes

Change the history command in reedline from **history to rlh** so as not to interfere with the nushell history command.

# reedline `\|/`

A readline replacement written in Rust

## Example (Simple REPL)

```rust
use reedline::{Reedline, DefaultPrompt, Signal};

let mut line_editor = Reedline::new();
let prompt = DefaultPrompt::default();

loop {
    let sig = line_editor.read_line(&prompt).unwrap();
    match sig {
        Signal::CtrlD | Signal::CtrlC => {
            line_editor.print_crlf().unwrap();
            break;
        }
        Signal::Success(buffer) => {
            // process `buffer`
            println!("We processed: {}", buffer);
        }
        Signal::CtrlL => {
            line_editor.clear_screen().unwrap();
        }
    }
}

```

## Are we prompt yet? (Development status)

This crate is currently under active development in JT's [live-coding streams](https://www.twitch.tv/jntrnr).
If you want to see a feature, jump by the streams, file an [issue](https://github.com/jonathandturner/reedline/issues) or contribute a [PR](https://github.com/jonathandturner/reedline/pulls)!

- [x] Basic unicode grapheme aware cursor editing.
- [x] Configurable prompt
- [x] Basic EMACS-style editing shortcuts.
- [ ] Advanced multiline unicode aware editing.
- [ ] Configurable keybindings.
- [x] Basic system integration with clipboard or optional stored history file.
- [ ] Content aware highlighting or validation.
- [ ] Autocompletion.

For a more detailed roadmap check out [TODO.txt](https://github.com/jonathandturner/reedline/blob/main/TODO.txt).

### Alternatives

For currently more mature Rust line editing check out:

- [rustyline](https://crates.io/crates/rustyline)
