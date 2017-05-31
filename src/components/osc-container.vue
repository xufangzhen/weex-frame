<template>
    <div class="root">
        <div v-if="ios" :style="{width: '750px', height: '40px', backgroundColor: backgroundColor}"></div>
        <osc-titlebar
                :dataRole="dataRole"
                :height="height"
                :backgroundColor="backgroundColor"
                :title="title"
                :titleColor="titleColor"
                :leftItemSrc="leftItemSrc"
                :leftItemTitle="leftItemTitle"
                :leftItemColor="leftItemColor"
                :rightItemSrc="rightItemSrc"
                :rightItemTitle="rightItemTitle"
                :rightItemColor="rightItemColor"
                @titleBarRightItemClick="titleBarRightItemClick"
                @titleBarLeftItemClick="titleBarLeftItemClick"></osc-titlebar>
        <div class="wrapper" :style="{top: ios ? (40 + height) : height}">
            <slot></slot>
        </div>
    </div>
</template>

<style scoped>
    .root {
        width: 750px;
        position: relative;
        display: flex;
        flex-direction: column;
    }
    .wrapper {
        width: 750px;
        position: absolute;
        top: 100px;
        bottom: 0;
    }
</style>

<script>
	import mixins from 'mixins'

	export default {
		mixins: [mixins],

		props: {
			dataRole: {default: 'none'},
			backgroundColor: {default: '#00000000'},
			height: {default: 110},
			title: {default: ''},
			titleColor: {default: 'white'},
			rightItemSrc: {default: ''},
			rightItemTitle: {default: ''},
			rightItemColor: {default: 'white'},
			leftItemSrc: {default: ''},
			leftItemTitle: {default: ''},
			leftItemColor: {default: 'white'}
		},

		methods: {
			titleBarRightItemClick (e) {
				this.$emit('titleBarRightItemClick', e)
			},

			titleBarLeftItemClick (e) {
				this.$emit('titleBarLeftItemClick', e)
			}
		}
	}
</script>
