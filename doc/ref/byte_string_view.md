### jsoncons::byte_string_view

```c++
#include <jsoncons/byte_string.hpp>

class byte_string_view;
```
A `byte_string_view` refers to a constant contiguous sequence of byte-like objects with the first element of the sequence at position zero.
It  holds two members: a pointer to constant `uint8_t*` and a size.

#### Member types

Member type                         |Definition
------------------------------------|------------------------------
`const_iterator`|
`iterator`|Same as `const_iterator`
`size_type`|`std::size_t`
`value_type`|`uint8_t`
`reference`|`uint8_t&`
`const_reference`|`const uint8_t&`
`difference_type`|`std::ptrdiff_t`
`pointer`|`uint8_t*`
`const_pointer`|`const uint8_t*`

#### Constructor

    constexpr byte_string_view() noexcept;

    constexpr byte_string_view(const uint8_t* data, std::size_t length) noexcept;

    template <class Container>
    constexpr explicit byte_string_view(const Container& cont); 

    byte_string_view(const byte_string_view&) noexcept = default;

    byte_string_view(byte_string_view&& other) noexcept;

#### Assignment

    byte_string_view& operator=(const byte_string_view& s) noexcept = default;

    byte_string_view& operator=(byte_string_view&& s) noexcept;

#### Iterators

    const_iterator begin() const noexcept;

    const_iterator end() const noexcept;

#### Element access

    constexpr const uint8_t* data() const noexcept;

    uint8_t operator[](size_type pos) const; 

    byte_string_view substr(size_type pos) const;

    byte_string_view substr(size_type pos, size_type n) const;

#### Capacity

    constexpr size_t size() const noexcept;

#### Non-member functions

    bool operator==(const byte_string_view& lhs, const byte_string_view& rhs);

    bool operator!=(const byte_string_view& lhs, const byte_string_view& rhs);

    template <class CharT>
    friend std::ostream& operator<<(std::ostream& os, const byte_string_view& o);

### Examples

#### Display bytes

```c++
std::vector<uint8_t> v = {'H','e','l','l','o'};
std::string s = {'H','e','l','l','o'};

std::cout << "(1) " << byte_string_view(v) << "\n\n";
std::cout << "(2) " << byte_string_view(s) << "\n\n";
```

Output:
```
(1) 48,65,6c,6c,6f

(2) 48,65,6c,6c,6f
```