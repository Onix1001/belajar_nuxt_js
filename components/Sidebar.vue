<template>
    <aside class=" w-52 h-screen top-0 left-0">
        <div class="py-2 px-2.5 text-lg flex justify-between items-center">
            <h1>Menu Utama</h1>
            <button>
                <Icon name="system-uicons:menu-hamburger" size="2rem" />
            </button>
        </div>
        <button class="dropdown-btn">
            <Icon name="fa6-solid:house" size="1rem" />
            <p>Master</p>
        </button>
        <button @click="toggleActive" class="dropdown-btn">
            <Icon name="fa6-solid:window-maximize" size="1rem" />
            <p>Barang</p>
        </button>
        <button @click="toggleActive" class="dropdown-btn">
            <Icon name="fa6-solid:users" size="1rem" />
            <p>Customer</p>
        </button>
        <button @click="toggleActive" class="dropdown-btn">
            <Icon name="fa6-solid:users" size="1rem" />
            <p>Supplier</p>
        </button>
        <button @click="toggleActive" class="dropdown-btn">
            <Icon name="fa6-solid:basket-shopping" size="1rem" />
            <p>Transaksi</p>
            <Icon class="chevron" name="fa6-solid:chevron-down" size="1rem" />
        </button>
        <div class="dropdown-container">
            <NuxtLink>
                <Icon name="fa6-solid:cart-shopping" />
                <p>Pembelian</p>
            </NuxtLink>
            <NuxtLink>
                <Icon name="fa6-solid:cart-shopping" />
                <p>Penjualan</p>
            </NuxtLink>
        </div>
        <button @click="toggleActive" class="dropdown-btn">
            <Icon name="fa6-solid:list-ul" size="1rem" />
            <p>Laporan</p>
            <Icon class="chevron" name="fa6-solid:chevron-down" size="1rem" />
        </button>
        <div class="dropdown-container">
            <NuxtLink>
                <Icon name="fa6-solid:calendar" />
                <p>Laporan Barang</p>
            </NuxtLink>
            <NuxtLink>
                <Icon name="fa6-solid:calendar" />
                <p>Laporan Pembelian</p>
            </NuxtLink>
            <NuxtLink>
                <Icon name="fa6-solid:calendar" />
                <p>Laporan Penjualan</p>
            </NuxtLink>
        </div>
    </aside>
</template>
<script>

export default {
    methods: {
        toggleActive(event) {
            event.target.classList.toggle('active')
            let dropdownContent = event.target.nextElementSibling
            dropdownContent.classList.toggle('show')
        }
    }
}
</script>