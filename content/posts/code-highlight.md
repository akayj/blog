---
title: "代码高亮"
date: 2019-12-03T16:19:07+08:00
draft: true
---

_Emacs_ style:

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
```

