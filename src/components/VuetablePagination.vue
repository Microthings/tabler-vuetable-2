<template>
  <ul v-show="tablePagination && tablePagination.last_page > 1" :class="css.wrapperClass">
    <li @click="loadPage(1)"
      :class="['', css.linkClass, isOnFirstPage ? css.disabledClass : '']">
        <i v-if="css.icons.first != ''" :class="[css.icons.first]"></i>
      <a class="page-link" href="javascript:void(0)" tabindex="-1" aria-disabled="true">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-chevrons-left" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
          <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
          <polyline points="11 7 6 12 11 17"></polyline>
          <polyline points="17 7 12 12 17 17"></polyline>
        </svg>
      </a>
    </li>
    <li @click="loadPage('prev')"
      :class="['', css.linkClass, isOnFirstPage ? css.disabledClass : '']">
        <i v-if="css.icons.next != ''" :class="[css.icons.prev]"></i>
      <a class="page-link" href="javascript:void(0)" tabindex="-1" aria-disabled="true">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><polyline points="15 6 9 12 15 18"></polyline></svg>
      </a>
    </li>
    <template v-if="notEnoughPages">
      <template v-for="n in totalPage">
        <li @click="loadPage(n)"
          :class="[css.pageClass, isCurrentPage(n) ? css.activeClass : '']"
          >
          <a class="page-link" href="javascript:void(0)" v-html="n"></a>
        </li>
      </template>
    </template>
    <template v-else>
      <template v-for="n in windowSize">
        <li @click="loadPage(windowStart+n-1)"
          :class="[css.pageClass, isCurrentPage(windowStart+n-1) ? css.activeClass : '']"
          >
          <a class="page-link" href="javascript:void(0)" v-html="windowStart+n-1"></a>
        </li>
      </template>
    </template>
    <li @click="loadPage('next')"
      :class="['', css.linkClass, isOnLastPage ? css.disabledClass : '']">
      <i v-if="css.icons.next != ''" :class="[css.icons.next]"></i>
      <a class="page-link" href="javascript:void(0)">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><polyline points="9 6 15 12 9 18"></polyline></svg>
      </a>
    </li>
    <li @click="loadPage(totalPage)"
      :class="['', css.linkClass, isOnLastPage ? css.disabledClass : '']">
      <i v-if="css.icons.last != ''" :class="[css.icons.last]"></i>
      <a class="page-link" href="javascript:void(0)">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-chevrons-right" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
          <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
          <polyline points="7 7 12 12 7 17"></polyline>
          <polyline points="13 7 18 12 13 17"></polyline>
        </svg>
      </a>
    </li>
  </ul>
</template>

<script>
import PaginationMixin from './VuetablePaginationMixin.vue'

export default {
  mixins: [PaginationMixin],
}
</script>
