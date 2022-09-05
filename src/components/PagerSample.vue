<template>
    <div>
        <pager :buttoncount="buttoncount" :cardsperpagecount="cardsperpagecount"></pager> 
    </div> 
</template>
<script>

import Pager from './Pager.vue';

export default {
    data () {
        return {
            buttoncount: 50,
            cardsperpagecount: 9,
        }
    },
    components: {
        Pager
    },
}
</script>