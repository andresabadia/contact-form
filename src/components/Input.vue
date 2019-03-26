<template>
    <div 
        class="container-parent" 
        :style="{
            height:height + 40 + 'px'
            }">
        <div 
            class="container" 
            :style="{
                height: height + 20 + 'px',
                width: width + 20 + 'px'
                }">
            <div 
                class="idx-input-div" :style="{
                    height:height + 'px',
                    width:width+'px'
                    }">                
                <app-border-1 :animate="animate" :height="height" :width="width"></app-border-1>
                <app-border-2 :animate="!animate" :height="height" :width="width"></app-border-2>
                <input v-if="!message" :type="type" class="idx-input" @focus="focus" @blur="blur" v-model="input">
                <textarea v-else :type="type" class="idx-textarea" @focus="focus" @blur="blur" v-model="input"></textarea>
                <div class="idx-input-placeholder" :class="inputLabel" @click="inputFocus">{{label}}</div>
            </div>
        </div>
    </div>
    
</template>

<script>
import InputBorder1 from './borders/InputBorder1.vue';
import InputBorder2 from './borders/InputBorder2.vue';
export default {
    data(){
        return{
            inputLabel: '',
            input:'',
            animate:false
        }
    },
    props: {
        label: String,
        type: {
            default: 'text'
        },
        height: {
            default: 40
        },
        width:{
            default: 200
        }
    },
    computed:{
        message(){
            if (this.type == 'message'){
                return true
            } else {
                return false
            }
        }
    },
    methods:{
        inputFocus(e){  
            e.target.previousElementSibling.focus()         
        },
        focus(){
            this.inputLabel='idx-input-label';
            this.animate = true;
        },
        blur(){
            this.input == '' ? this.inputLabel='':'';
            this.animate = this.input == '' ? false : true;
        }
    },
    components:{
        appBorder1: InputBorder1,       
        appBorder2: InputBorder2
    }

}
</script>


<style scoped>
    *{  
    box-sizing: border-box;
    }
    .container-parent{
        display: flex;
        width: 100%;
        justify-content: center;
        align-items: center;
        background:azure;
        height: 80px;
    }
    .container{
        display: flex;
        height: 60px;
        width: 220px;
        justify-content: center;
        align-items: center;
        background:white;
    
    }
    .idx-input-div{
        position: relative;
        height: 40px;
        width: 200px;      
    }
    .idx-input, .idx-textarea{
        position:absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        padding: 0 10px;
        border:none;
    }
    .idx-textarea{        
        padding: 10px;
        resize: none;
    }
    .idx-input:focus, .idx-textarea:focus{
        outline: none;
    }
    .idx-input-placeholder{
        position: absolute;
        top: 0;
        left: 0;
        line-height: 40px;
        color:rgba(118, 161, 255, 0.562);  
        padding: 0 10px;
        z-index: 1;
        transition: .3s;
    }
    .idx-input-label{
        transform: scale(.75) translateY(-20px);
        background: white;
        color:rgb(118, 161, 255);
        height: 30px;
    }
</style>
