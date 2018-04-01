# Yocto Project

Yocto Project for modern hi-tech products

---

### Agenda

- Yocto advantages
- Current status and what's next
- Live demo (optional)

---

### How to create `base_blob` from `char*` string?

```
char *str = "0x12345678"
base_blob<64> bb;
bb.SetHex(str);
```

---

![Flux Explained](https://facebook.github.io/flux/img/flux-simple-f8-diagram-explained-1300w.png)
