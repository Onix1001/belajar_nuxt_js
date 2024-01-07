<script setup>
const data = useData()
</script>
<template>
    <div class="w-full overflow-hidden">
        <Topbar title="Data Dashboard" />
        <div class="p-3 home ">
            <form @submit.prevent="handleSubmit" class="grid grid-cols-2 gap-2 " id="formBarang">
                <label for="barang">Barang :<input id="barang" type="text" name="barang" required></label>
                <label for="satuan">Satuan :<input id="satuan" type="text" name="satuan" required></label>
                <label for="hargaBeli">Harga Beli :<input id="hargaBeli" type="number" name="hargaBeli" required></label>
                <label for="hargaJual">Harga Jual :<input id="hargaJual" type="number" name="hargaJual" required></label>
                <button type="submit" class="border-2 border-blue-500">Submit</button>
            </form>
        </div>
        <ClientOnly>
            <div class="bg-zinc-100 h-screen p-3">
                <div class="flex flex-col">
                    <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
                        <div class="inline-block min-w-full py-2 sm:px-6 lg:px-8">
                            <div class="overflow-hidden">
                                <table class="min-w-full text-left text-sm font-light">
                                    <thead class="border-b bg-white font-medium text-center">
                                        <tr>
                                            <th scope="col" class="px-6 py-4">#</th>
                                            <th scope="col" class="px-6 py-4">Barang</th>
                                            <th scope="col" class="px-6 py-4">Satuan</th>
                                            <th scope="col" class="px-6 py-4">Harga Beli</th>
                                            <th scope="col" class="px-6 py-4">Harga Jual</th>
                                            <th scope="col" class="px-6 py-4">Aksi</th>
                                        </tr>
                                    </thead>
                                    <tbody v-for="(data, index) in data" :key="index">
                                        <tr class="border-b bg-neutral-100 text-center">
                                            <td class="whitespace-nowrap px-6 py-4 font-medium">{{ index }}</td>
                                            <td class="whitespace-nowrap px-6 py-4">{{ data.barang }}</td>
                                            <td class="whitespace-nowrap px-6 py-4">{{ data.satuan }}</td>
                                            <td class="whitespace-nowrap px-6 py-4">{{ data.hargaBeli }}</td>
                                            <td class="whitespace-nowrap px-6 py-4">{{ data.hargaJual }}</td>
                                            <td class="whitespace-nowrap px-6 py-4"><button @click="deleteData"
                                                    class="bg-red-600 text-white px-6 py-2 rounded-lg hover:bg-red-700">delete</button>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </ClientOnly>
    </div>
</template>
<script>
export default {
    methods: {
        setData(item) {
            if (item) {
                let data = useData();
                data.value.push(item);
            }
        },
        handleSubmit(event) {
            const formData = new FormData(formBarang)
            const values = [...formData.entries()];

            this.setData(Object.fromEntries(values))
            formBarang.reset()
        },
        deleteData(index) {
            let data = useData()
            data.value.splice(index, 1)
        }
    }
}
</script>