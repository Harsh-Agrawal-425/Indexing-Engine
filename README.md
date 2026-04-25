# IndexEngine

Database indexing simulation and analysis engine implementing 8 major indexing strategies from CS315 Database Systems.

## Index Structures

| # | Index | Type | Key Characteristics |
|---|-------|------|---------------------|
| 1 | Sorted Array | Ordered | Binary search O(log n); O(n) insert/delete |
| 2 | Chained Hash | Hash | Separate chaining; auto-rehash at load > 0.75 |
| 3 | Linear Probing | Hash | Open addressing; tombstone deletion |
| 4 | Extendible Hash | Hash | Dynamic directory; local/global depth split |
| 5 | Bitmap | Bitmap | Bitvector per distinct value; AND/OR queries |
| 6 | B-Tree | Tree | Keys + data in all nodes; CLRS-style delete |
| 7 | B+-Tree | Tree | Data only in linked leaves; range queries |
| 8 | R-Tree | Spatial | MBR-based; quadratic split; range queries |

## Build & Run

```bash
# Build
cd me2
cmake -B build
cmake --build build

# Run correctness tests
./build/test_all

# Run benchmarks (generates CSV)
./build/benchmark_all

# View report
cat results/benchmark_report.csv
```

## Benchmarks

Measures for each index at N = 1K, 10K, 100K:
- **Search time** (microseconds)
- **Modification overhead** — insert + delete time (microseconds)
- **Space overhead** — heap memory after all inserts (bytes)

Results are written to `results/benchmark_report.csv`.

## Project Structure

```
me2/
├── CMakeLists.txt
├── include/          # Header files for all index structures
├── src/              # Implementation files
├── tests/            # Correctness test suite
├── benchmarks/       # Benchmark harness
└── results/          # Generated CSV reports
```
