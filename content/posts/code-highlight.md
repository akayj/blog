---
title: "代码语法高亮"
date: 2019-12-03T16:19:07+08:00
---

```go
// GetTitleFunc returns a func that can be used to transform a string
// title case.
//
// The supported styles are
//
// - "Go" (strings.Title)
//
// If an unknown or empty style is provided, AP style is what you get.
func GetTitleFunc(style string) func(s string) string {
	switch strings.ToLower(style) {
		case "go":
			return strings.Title
		default:
			return transform.NewTitleConverter(transform.APStyle)
	}
}

// waitSignal regist quit signals, a done channel is returned
// as signal receiver
func waitSignal() <-chan os.Signal {
    sigs := make(chan os.Signal, 1)
    done := make(chan os.Signal)

    signal.Notify(sigs, syscall.SIGINT, syscal.SIGTERM)

    go func() {
        sig := <- sigs
        done <- sig
    }()

    return done
}
```
