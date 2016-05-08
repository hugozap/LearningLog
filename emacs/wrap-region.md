# wrap-region

Enable with (wrap-region-mode t) inside the init file

Select a region and type { or other special characters to
enclose it.

## Add characters and set the mode they apply to

```elisp

(wrap-region-add-wrapper "$" "$")
(wrap-region-add-wrapper "{-" "-}" "#")
(wrap-region-add-wrapper "/" "/" nil 'ruby-mode)
(wrap-region-add-wrapper "/* " " */" "#" '(java-mode javascript-mode css-mode))
(wrap-region-add-wrapper "`" "`" nil '(markdown-mode ruby-mode))

```

The same can be done with:

```elisp
(wrap-region-add-wrappers
 '(("$" "$")
   ("{-" "-}" "#")
   ("/" "/" nil ruby-mode)
   ("/* " " */" "#" (java-mode javascript-mode css-mode))
   ("`" "`" nil (markdown-mode ruby-mode))))

```

https://github.com/rejeep/wrap-region.el