<template>
  <div class="container py-5 px-md-5">
    <ul class="list-group">
      <li
        v-for="item in shopStore.cart"
        :key="item.id"
        class="list-group-item d-flex justify-content-between align-items-center ps-0"
      >
        <div>
          <button
            class="btn btn-text"
            @click="shopStore.deleteFromCart(item.id)"
          >
            <i class="bi bi-x"></i>
          </button>
          {{ item.brand }} {{ item.model }}
        </div>
        <div class="d-flex align-items-center">
          <span v-price="item.price * item.quantity" />
          <input
            type="number"
            min="1"
            class="form-control ms-2"
            v-model.number="item.quantity"
            @change="shopStore.saveCart()"
          />
        </div>
      </li>

      <li class="list-group-item text-end">
        Итого:
        <span v-price="shopStore.cartTotal" />
      </li>
    </ul>

    <div class="d-flex justify-content-between mt-3" v-if="shopStore.cartTotal">
      <button class="btn btn-warning" @click="shopStore.clearCart">
        Очистить корзину
      </button>

      <router-link class="btn btn-success" to="/shop/checkout">
        Оформить заказ
      </router-link>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
input[type="number"] {
  width: 70px;
}
</style>
