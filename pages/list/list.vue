<template>
	<view>
		<unicloud-db ref="udb"
		 v-slot:default="{data, loading, error, options}" collection="contacts">
			<view v-if="error">{{error.message}}</view>
			<view v-else>
				<uni-list>
					<uni-list-item v-for="item in data" 
					:key="item._id" :title="item.name" :note="item.phone" 
					@click.native="rmItem(item._id)"
					link></uni-list-item>
				</uni-list>
			</view>
		</unicloud-db>
	</view>
</template>

<script>
	export default {
		name: 'list',
		data() {
			return {
				
			}
		},
		methods: {
			rmItem(id) {
				console.log('fuck id', id)
				this.$refs.udb.remove(id)
			}
		}
	}
</script>

<style>

</style>
