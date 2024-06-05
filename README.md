# str
Tentu, berikut adalah penjelasan tentang diagram kelas dalam bahasa Indonesia:

### Ikhtisar Diagram Kelas

Diagram kelas ini menggambarkan struktur dari sistem rute penerbangan. Diagram ini menunjukkan kelas-kelas yang terlibat, atribut, metode, dan hubungan di antara mereka. Berikut adalah penjelasan dari setiap kelas dan hubungannya:

#### 1. `FlightNode`
- **Atribut:**
  - `string nme`: Ini mewakili nama dari node penerbangan (kota dalam konteks ini).
- **Metode:**
  - `FlightNode(const string &cityNme)`: Konstruktor untuk menginisialisasi node dengan nama kota.
  - `virtual ~FlightNode()`: Destruktor virtual.
  - `string getNme() const`: Metode untuk mendapatkan nama dari node penerbangan.

#### 2. `FlightGrph` (Kelas Abstrak)
- **Metode:**
  - `virtual ~FlightGrph()`: Destruktor virtual.
  - `virtual void ddNode(FlightNode *node) = 0`: Metode virtual murni untuk menambahkan node.
  - `virtual void ddEdge(int node1Index, int node2Index) = 0`: Metode virtual murni untuk menambahkan edge (rute) antara dua node.
  - `virtual void disply() const = 0`: Metode virtual murni untuk menampilkan graf.

#### 3. `FlightGrphAdjMtrx` (Turunan dari `FlightGrph`)
- **Atribut:**
  - `int nodeCount`: Menghitung jumlah node dalam graf.
  - `vector<FlightNode *> nodes`: Vektor yang menyimpan node-node penerbangan.
  - `vector<vector<int>> djacencyMtrx`: Matriks ketetanggaan yang menyimpan informasi tentang konektivitas antara node-node.
- **Metode:**
  - `FlightGrphAdjMtrx(int size)`: Konstruktor untuk menginisialisasi graf dengan ukuran tertentu.
  - `virtual ~FlightGrphAdjMtrx()`: Destruktor.
  - `void ddNode(FlightNode *node)`: Metode untuk menambahkan node ke graf.
  - `void ddEdge(int node1Index, int node2Index)`: Metode untuk menambahkan edge antara dua node.
  - `void disply() const`: Metode untuk menampilkan graf.

#### 4. `flightTransRoute`
- **Atribut:**
  - `string strtLocation`: Lokasi awal dari rute penerbangan.
  - `string endLocation`: Lokasi akhir dari rute penerbangan.
- **Metode:**
  - `flightTransRoute(const string &strt, const string &end)`: Konstruktor untuk menginisialisasi rute dengan lokasi awal dan akhir.

#### 5. `flightRoute` (Turunan dari `FlightGrphAdjMtrx`)
- **Metode:**
  - `flightRoute(int size)`: Konstruktor untuk menginisialisasi rute penerbangan dengan ukuran tertentu.
  - `int findNodeIndex(const string &nodeNme)`: Metode untuk menemukan indeks dari node berdasarkan nama.
  - `void displyShortestRoute(const string &strtLocation, const string &endLocation)`: Metode untuk menampilkan rute terpendek antara dua lokasi.
  - `void displyAllRoutes(const string &strtLocation, const string &endLocation)`: Metode untuk menampilkan semua rute antara dua lokasi.
  - `void deleteRoute(int node1Index, int node2Index)`: Metode untuk menghapus rute antara dua node.
  - `void ddRoute(int node1Index, int node2Index)`: Metode untuk menambahkan rute antara dua node.
  - `void displyAdjacencyMtrx() const`: Metode untuk menampilkan matriks ketetanggaan.

- **Metode Internal:**
  - `void dfs(int currentNode, int trgetNode, vector<int> &visited, vector<int> &pth, bool &found)`: Metode untuk melakukan pencarian DFS.
  - `int minDistnce(const vector<int> &distnce, const vector<bool> &visited)`: Metode untuk menemukan jarak minimum.
  - `void printShortestRoute(int strt, int end, const vector<int> &prnt)`: Metode untuk mencetak rute terpendek.
  - `void dfsAllRoutes(int currentNode, int trgetNode, vector<int> &visited, vector<int> &pth)`: Metode untuk melakukan pencarian DFS untuk semua rute.
  - `void printRouteHeader() const`: Metode untuk mencetak header rute.
  - `void printDeletedRoute(int node1Index, int node2Index)`: Metode untuk mencetak informasi tentang rute yang dihapus.
  - `void printAddedRoute(int node1Index, int node2Index)`: Metode untuk mencetak informasi tentang rute yang ditambahkan.

### Hubungan Antar Kelas
- `FlightGrph` adalah kelas abstrak yang diturunkan oleh `FlightGrphAdjMtrx`.
- `FlightGrphAdjMtrx` adalah kelas konkret yang mengimplementasikan metode dari `FlightGrph`.
- `flightRoute` adalah kelas yang diturunkan dari `FlightGrphAdjMtrx` dan memperluas fungsionalitasnya.
- `FlightNode` memiliki hubungan agregasi dengan `FlightGrphAdjMtrx` dan `flightRoute`.
- `flightTransRoute` memiliki hubungan asosiasi dengan `flightRoute`.

Diagram ini memberikan gambaran lengkap tentang bagaimana objek dan data dalam sistem rute penerbangan ini berinteraksi dan saling berhubungan.
