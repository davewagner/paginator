<template>
        <div>
            <ul class="pagination" id="pager" />
        </div> 
</template>
<script>

export default {
    mounted() {
        for (let i = 0; i < this.buttoncount; i++)
            this.createPagerButtons()
    }, 
    props: {
        buttoncount: {
            required: true,
            type: Number
        }, 
        cardsperpagecount: {
            required: true,
            type: Number
        }
    },
    data () {
        return {
            cnt: 1,
            idx: 0
        }
    },
    methods: {
        createPagerButtons() {
            var ul = document.getElementById("pager");
                console.log("got ul reference " + ul)
            var li = document.createElement("li");
            if (this.cnt == 1) {
                li.setAttribute("class","option page-link pageSelected");
                li.setAttribute("idx", this.idx++);
            } else {
                li.setAttribute("class","option page-link");
                li.setAttribute("idx", this.idx++ * this.cardsperpagecount);
            }
            
            li.appendChild(document.createTextNode(this.cnt++));
            li.addEventListener("click", this.loadNextCards)
            ul.appendChild(li);
        },
        loadNextCards(e) {
            var items = document.getElementsByClassName("option");
            for (let i = 0; i < items.length; i++) {
                items[i].classList.remove("pageSelected");
            }
            e.target.classList.add("pageSelected")
        }
    }
}
</script>
<style>
.pageSelected {
    background-color: coral;
}
    @import 'https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css';
</style>