#include <algorithm>
#include <cstddef>
#include <memory>

template<typename T>
struct RawMemory {
public:
    T* buf = nullptr;
    size_t cp = 0;

    static T* Allocate(size_t n) {
        return static_cast<T*>(operator new(n * sizeof(T)));
    }

    static void Deallocate(T* buf) {
        operator delete(buf);
    }

    void swap(RawMemory& other) noexcept {
        std::swap(buf, other.buf);
        std::swap(cp, other.cp);
    }

    RawMemory() = default;

    RawMemory(size_t n) {
        buf = Allocate(n);
        cp = n;
    }

    RawMemory(const RawMemory&) = delete;

    RawMemory(RawMemory&& other) noexcept {
        swap(other);
    }

    ~RawMemory() {
        Deallocate(buf);
    }

    RawMemory& operator = (const RawMemory&) = delete;

    RawMemory& operator = (RawMemory&& other) noexcept {
        swap(other);
        return *this;
    }

    const T* operator + (size_t i) const {
        return buf + i;
    }

    T* operator + (size_t i) {
        return buf + i;
    }

    const T& operator[] (size_t i) const {
        return buf[i];
    }

    T& operator[] (size_t i) {
        return buf[i];
    }
};

template<typename T>
class Vector {
    RawMemory<T> data;
    size_t sz = 0;

public:
    Vector() = default;

    Vector(size_t n) : data(n) {
        std::uninitialized_value_construct_n(data.buf, n);
        sz = n;
    }

    Vector(const Vector& other) : data(other.sz) {
        std::uninitialized_copy_n(other.data.buf, other.sz, data.buf);
        sz = other.sz;
    }

    Vector(Vector&& other) noexcept {
        swap(other);
    }

    ~Vector() {
        std::destroy_n(data.buf, sz);
    }

    Vector& operator=(const Vector& other) {
        if (other.sz > data.cp) {
            Vector tmp(other);
            swap(tmp);
        }
        else {
            for (size_t i = 0; i < sz && i < other.sz; ++i) {
                data[i] = other.data[i];
            }
            if (sz < other.sz) {
                std::uninitialized_copy_n(other.data.buf + sz, other.sz - sz, data.buf);
            }
            else if (sz > other.sz) {
                std::destroy_n(data.buf + other.sz, sz - other.sz);
            }
            sz = other.sz;
        }
        return *this;
    }

    Vector& operator=(Vector&& other) noexcept {
        swap(other);
        return *this;
    }

    void reserve(size_t n) {
        if (n > data.cp) {
            RawMemory<T> new_data(n);
            std::uninitialized_move_n(data.buf, sz, new_data.buf);
            std::destroy_n(data.buf, sz);
            data = std::move(new_data);
        }
    }

    void resize(size_t n) {
        reserve(n);
        if (sz < n) {
            std::uninitialized_value_construct_n(data + sz, n - sz);
        }
        else if (sz > n) {
            std::destroy_n(data + n, sz - n);
        }
        sz = n;
    }

    void swap(Vector& other) noexcept {
        data.swap(other.data);
        std::swap(sz, other.sz);
    }

    void push_back(const T& elem) {
        if (sz == data.cp) {
            reserve(sz == 0 ? 1 : sz * 2);
        }
        new (data + sz) T(elem);
        ++sz;
    }

    void pop_back() {
        std::destroy_at(data + sz - 1);
        --sz;
    }

    size_t size() const {
        return sz;
    }

    size_t capacity() const {
        return data.cp;
    }

    T& operator[] (size_t i) {
        return data[i];
    }

    const T& operator[] (size_t i) const {
        return data[i];
    }

    T* begin() {
        return data.buf;
    }

    T* begin() const {
        return data.buf;
    }

    T* end() {
        return data.buf + sz;
    }

    T* end() const {
        return data.buf + sz;
    }

    void clear() {
        for (size_t i = 0; i < sz; ++i) {
            data[i].~T();
        }
        sz = 0;
    }
};
