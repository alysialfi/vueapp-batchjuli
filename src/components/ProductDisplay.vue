<script>
    export default {
        name: 'ProductDisplay',
        data() {
            return {
                price: 75,
                amount: 0,
                // subTotal: 0,
                isAmountGreaterThan3: false,
                // colors: [ 'bg-red-500', 'bg-blue-500', 'bg-grey-500' ],
                colors:  [
                    {
                        name: 'merah',
                        color: 'bg-red-500',
                        price: 75,
                    },
                    {
                        name: 'biru',
                        color: 'bg-blue-500',
                        price: 85
                    },
                    {
                        name: 'abu-abu',
                        color: 'bg-gray-500',
                        price: 95
                    }
                ]
            }
        },
        methods: {
            addToCart() {
                if (this.amount > 3) {
                    this.isAmountGreaterThan3 = true
                }
            },
            changePrice(clickedColor) {
                const chosenColorObject = this.colors.find((c) => c.name === clickedColor)
                this.price = chosenColorObject.price
            }
        },
    }
</script>

<template>
    <div class="flex w-full">
        <div class="w-1/2 h-screen bg-gray-200">
            <!-- thumbnail -->
            <img src="../assets/images/sofa.png" alt="sofa thumbnail">
        </div>
        <div class="w-1/2">
            <!-- details -->
            <div>
                <!-- title & desc -->
                <h1>Greyana Sofa</h1>
                <p>
                    Introducing the Greyana Sofa. The perfect combination of style and comfort. With its sleek and modern design, this sofa is a statement piece that will elevate any living space. The Greyana Sofa features a stunning grey upholstery that is both soft to the touch and durable for everyday use. Crafted with a sturdy wooden frame and high-density foam cushions, the Greyana Sofa offers unbeatable comfort and support. The seat and back cushions are also removable and reversible, making it easy to maintain and keep looking like new.
                </p>
                <div class="mt-10 flex gap-2 w-full">
                    <div @click="changePrice(color.name)" v-for="(color) in colors" :key="color.name" class="flex gap-1 items-center cursor-pointer">
                        <div :class="color.color" class="w-4 h-4 rounded-full"></div>
                        {{ color.name }}
                    </div>
                </div>
            </div>
            <div>
                <!-- price, counter, & bubtton -->
                <div class="text-3xl font-semibold">
                    ${{ price }}
                </div>
                <div class="flex mt-2">
                    <button @click="amount--" class="bg-black text-white px-2">-</button>
                    <div class="border border-black px-5 bg-gray-100">{{ amount }}</div>
                    <button @click="amount++" class="bg-black text-white  px-2">+</button>
                </div>
                <p v-if="isAmountGreaterThan3">maximum items that can be added is 3</p>
                <div class="text-xl font-semibold mt-10">Subtotal: ${{ price * amount }}</div>
                <div class="flex w-full justify-between items-center gap-5 mt-2 mr-5">
                    <button class="text-center w-full bg-black text-white py-4">Buy Now</button>
                    <button @click="addToCart()" class="text-center w-full bg-black text-white py-4">Add To Cart</button>
                </div>
            </div>
        </div>
    </div>
</template>