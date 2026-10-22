Android RecyclerView Sample (Droid Desserts)
Proyek Android sederhana ini mendemonstrasikan cara mengimplementasikan komponen RecyclerView di Kotlin untuk menampilkan daftar item secara dinamis dan efisien pada aplikasi Android.

🚀 Fitur Utama
RecyclerView & LayoutManager: Menggunakan LinearLayoutManager untuk menyusun item daftar secara vertikal.

Custom Adapter: Menghubungkan sumber data (DataSet) ke tampilan antarmuka (View).

View Holder Pattern: Mengoptimalkan performa rendering dengan menyimpan referensi komponen UI dari setiap item.

🛠️ Detail Arsitektur & Komponen Teknis
Proyek ini dibangun menggunakan struktur komponen standar Android modern:

MainActivity.kt:

Titik masuk utama aplikasi.

Menginisialisasi komponen RecyclerView dari file layout XML.

Menyiapkan data dummy (daftar item teks dari Item 0 hingga Item 9) dan memasangkannya ke Adapter.

CustomAdapter.kt:

Kelas turunan dari RecyclerView.Adapter.

Bertanggung jawab untuk mengubah (inflate) layout item XML (card_view_design atau sejenisnya) dan memetakan data teks ke dalam ViewHolder.

Layout XML (activity_main.xml & card_view_design.xml):

Wadah utama penampung daftar komponen.

Desain tata letak per baris item teks sederhana.

💻 Contoh Potongan Kode Teknis
1. Inisialisasi RecyclerView di MainActivity
Kotlin
val recyclerView: RecyclerView = findViewById(R.id.recyclerView)
recyclerView.layoutManager = LinearLayoutManager(this)

// Contoh data list item
val itemList = listOf("Item 0", "Item 1", "Item 2", "Item 3", "Item 4", "Item 5", "Item 6", "Item 7", "Item 8", "Item 9")
recyclerView.adapter = CustomAdapter(itemList)
2. Implementasi CustomAdapter
Kotlin
class CustomAdapter(private val mList: List<String>) : RecyclerView.Adapter<CustomAdapter.ViewHolder>() {

    class ViewHolder(ItemView: View) : RecyclerView.ViewHolder(ItemView) {
        val textView: TextView = itemView.findViewById(R.id.textView)
    }

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(R.layout.card_view_design, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder.textView.text = mList[position]
    }

    override fun getItemCount(): Int = mList.size
}
