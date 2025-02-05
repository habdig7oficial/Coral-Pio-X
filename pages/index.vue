<template>
<tr v-for="route in $router.options.routes">
          <td>
            <nuxt-link :to="route.path">{{route.path}}</nuxt-link>
          </td>
        </tr>
</template>