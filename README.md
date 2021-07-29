# Find First Entry in List with Duplicates

        package main

        import (
            "errors"
            "fmt"
        )

        // Naive algorithm
        // O(n) time
        // O(1) memory
        func findNaive(a []int, target int) (int, error) {
            for i := 0; i < len(a); i++ {
                if a[i] == target {
                    return a[i], nil
                }
            }
            return -1, errors.New("Have not mutches")
        }

        // Binary algorithm
        // O(log n) time
        // O(1) memory
        func findBinary(a []int, target int) int {
            low := 0
            high := len(a) - 1
            var mid int

            for low <= high {
                mid = (low + high) / 2

                if a[mid] < target {
                    low = mid + 1
                } else if a[mid] > target {
                    high = mid - 1
                } else {
                    if mid-1 < 0 {
                        return mid
                    }
                    if a[mid-1] != target {
                        return mid
                    }
                    high = mid - 1
                }

            }
            return -1
        }

        func main() {
            A := []int{-14, -10, 2, 108, 108, 243, 285, 285, 285, 401}
            target := 108
            x := findBinary(A, target)
            fmt.Println(x)
        }
