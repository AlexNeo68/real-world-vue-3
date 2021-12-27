<template>
  <div>
    <h1>Erorr for connect</h1>
    <p>Please <router-link @click.prevent="$router.go(-1)">try</router-link> again</p>
  </div>
</template>