# Yocto Project

Yocto Project for modern hi-tech products

---

### Agenda

- Yocto advantages
- Current status and what's next
- Live demo (optional)

---

### `uint256`

```
template<unsigned int BITS>
class base_blob
{
protected:
    static constexpr int WIDTH = BITS / 8;
    uint8_t data[WIDTH];

public:
    base_blob() {
        memset(data, 0, sizeof(data));
    }

    void SetHex(const char* psz);
};
```

---

### `uint256` - `SetHex()`
```
template <unsigned int BITS>
void base_blob<BITS>::SetHex(const char* psz)
{
    memset(data, 0, sizeof(data));

    const char* pbegin = psz;
    unsigned char* p1 = (unsigned char*)data;
    unsigned char* pend = p1 + WIDTH;

    while (psz >= pbegin && p1 < pend) {
        *p1 = ::HexDigit(*psz--);
        if (psz >= pbegin) {
            *p1 |= ((unsigned char)::HexDigit(*psz--) << 4);
            p1++;
        }
    }
}
```

---

### `base_blob` from `char*` string?

```
char *str = "0x12345678"
base_blob<64> bb;
bb.SetHex(str);
```

- [github link](https://github.com/kostaz/playground/blob/master/cpp/convert_bytes_to_string.cpp)
- [ideone link](https://ideone.com/CeDilU)
- [tio link](https://tio.run/##tVVNb9swDL37V3DYENv5zpqkXZvksst22qG9FUUgy3RizJE8WTbSFfnryyhFTl2s38B0eBAl6pF8omye5z2eMbHa7z@mgmdljDBLZaEVss3Cu1@rkGupmiuFjlOh@@uF5w0G8FVu8jRjOpXi3NirTgfWuCWiPs9z6Eln0Z7Z/i7yUkOwZirucRljHNpTJTGeLTXETLPrG5jD3XDLki4Mt9GpwbGdT6a7C8fzo9REZM9@gv7gGAMm03ESnbLE@HmDdtuDNuUoKlQaUo2KAkQZQoG/ShQcQSbH4KkAheRY0KqKUfXp7MDTuMmpPpzp2xwF2yBcLTzS4PycIqZiBd9we6lVwKUoNFy1KEqEq1R0obGCIu5CJGUGyWXOOBbzhGUFht6dBzSadKq68NwiqcodCyfFjJIbll@PplYhf@h3wR8Z@GzgxMDYwMTA1MCp37VcLw3/zHh/McAMRAa4gdgAGkj8nctMVX2FBaoKg8DW1nM1h@2T0PkkUkFwRaVTqm73wlgf5gc5jNHphNb37phjfRUVy@hc4MwwaKe6JjYjTSCouSw1tFq1suGDginVvCzWy4jxn4EPfpPlwZ7TlgIvFuMbcnvBqzWa1F47pwrqUgl7f7t/Wu/wjEBLcNf8hmZLRZYKhOd6ruLr5/rLpeZOkXNfWdmCsAvWogsx81pCWwFpDxtmnB7rUqyWNHVqUrHvHgeh75ViSrHb5rO0mt1HfkQ4SzDwmg30ig@JU8bWQY5OHBvKBVgePhhSzRxtexEYYuhAkf5GmVgrDJ94Y6@hCsPjaydnLunjOJsds6KpXafryf6D1JbbdeZ7BW9w1KUtoHpOeDB/jU5nNCI6YJGs8ImrqN6qjWvzIbXvfv@HJxlbFfseec05xRv/BQ)

---

![Flux Explained](https://facebook.github.io/flux/img/flux-simple-f8-diagram-explained-1300w.png)
