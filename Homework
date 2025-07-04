class MyDict:
    def __init__(self):
        self.size = 100
        self.data = [[] for _ in range(self.size)]

    def _hash(self, key):
        return sum(ord(c) for c in str(key)) % self.size

    def set(self, key, value):
        h = self._hash(key)
        for pair in self.data[h]:
            if pair[0] == key:
                pair[1] = value
                return
        self.data[h].append([key, value])

    def get(self, key, default=None):
        h = self._hash(key)
        for pair in self.data[h]:
            if pair[0] == key:
                return pair[1]
        return default

    def pop(self, key, default=None):
        h = self._hash(key)
        for i, pair in enumerate(self.data[h]):
            if pair[0] == key:
                return self.data[h].pop(i)[1]
        return default

    def keys(self):
        return [pair[0] for bucket in self.data for pair in bucket]

    def values(self):
        return [pair[1] for bucket in self.data for pair in bucket]

    def items(self):
        return [(pair[0], pair[1]) for bucket in self.data for pair in bucket]

    def clear(self):
        self.data = [[] for _ in range(self.size)]

    def copy(self):
        new_dict = MyDict()
        for key, value in self.items():
            new_dict.set(key, value)
        return new_dict


if name == "__main__":
    d = MyDict()
    d.set("apple", 10)
    d.set("banana", 20)
    print("apple:", d.get("apple"))            # 10
    print("pear (нету):", d.get("pear"))       # None
    print("Все ключи:", d.keys())              # ['apple', 'banana']
    print("Все значения:", d.values())         # [10, 20]
    print("Все пары:", d.items())              # [('apple', 10), ('banana', 20)]

    d.set("apple", 99)
    print("Обновлённая apple:", d.get("apple"))  # 99

    print("Удаляем apple:", d.pop("apple"))     # 99
    print("После удаления:", d.get("apple"))    # None

    print("Копия словаря:")
    d_copy = d.copy()
    print(d_copy.items())

    d.clear()
    print("После очистки:", d.items())         # []
