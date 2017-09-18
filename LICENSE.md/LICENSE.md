def max_heapify(A, n, i):
    l = 2 * i
    r = 2 * i + 1
    largest = i
    if l <= n and A[i] < A[l]:
        largest = l
    if r <= n and A[largest] < A[r]:
        largest = r
    if largest != i:
        A[i], A[largest] = A[largest], A[i]
        max_heapify(A, n, largest)


def build_max_heap(A, n):
    for i in range(n // 2 - 1, 0, -1):
        max_heapify(A, n, i)


def heap_sort(A, n):
    build_max_heap(A, n)
    for i in range(len(A[1:]), 1, -1):
        A[i], A[1] = A[1], A[i]
        n = n - 1
        max_heapify(A, n, 1)


def main():
    A = [0, 16, 4, 10, 14, 7, 9, 3, 2, 8, 1]
    n = len(A[1:])
    heap_sort(A, n)
    print(A[1:])


if __name__ == '__main__':
    main()
