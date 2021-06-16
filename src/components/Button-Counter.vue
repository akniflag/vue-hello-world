<template>
    <div>
    <!-- <button @click="count++">You Clicked me {{count}} times</button> -->
    <button @click="counter">{{title}} You Clicked me {{count}} times {{alt}}</button>
    <!-- <img :src="alt"> -->
    <button @click="$emit('hungry')">告诉父组件，你想干啥</button>

    <!-- 是否选中的值 $event.target.checked  @change="$emit('changeOne',$event.target.value)" -->
    <!-- @input="$emit('input',$event.target.value)" -->
    <input type="checkbox" :checked = "checked"  @change="$emit('changeOne',$event.target.checked)">
    <div>
        {{checked}}
    </div>
    <br/>
    <div>
        <slot></slot>
        <!-- 如何访问组件内data，slotProps->u->bind data -->
        <slot name="usb1" :u="user">
            default slot value in usb1
        </slot>
        <br/>
        <slot name="usb2"></slot>

        <!-- 自定义插槽属性，user,u 可被template模版访问组件内data v-slot：hdmi="{user,u}"" -->
        <slot name="hdmi" :user="user" :u="user">
        </slot>
    </div>
    </div>
</template>

<script>
    export default {
        name:'ButtonCounter',
        // data(){
        //     return {
        //         count:0
        //     }
        // }
        data:()=>({
            count:0,
            user:{
                fn:"bill",
                ln:"gates"
            },
            value:true
        }),
        props:{
            title:String,
            alt:String,
            checked:{
                type:Boolean,
                default:true
            }
        },
        methods:{
            counter:function(){
                var that = this
                that.count++
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>