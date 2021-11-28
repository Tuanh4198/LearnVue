<template>
  <div class="hello" :id="id">
		<input type="text" v-model="name" placeholder="name"/>
		<button @click="selected = !selected">select</button>
		<button @click="isShow = !isShow">Toggle</button>
		<p v-show="isShow" :class="{selected: selected}">
			{{ name }}
		</p>
		<hr/>
		
		<input type="text" v-model="isWatch" placeholder="is Watch value change"/>
		<hr/>
		
		<button @click="aFunc()">Call a Function</button>
		<hr/>

		<div v-for="(task, index) in tasks" :key="index">
			{{ task }}
		</div>
		<hr/>

		<Task 
			v-for="(task, index) in tasks" 
			:key="index" 
			:taskData="task"
			:taskIndex="index"
		/>
		<hr/>

		<input type="text" v-model="$store.state.name" placeholder="name"/>
		<p>{{ $store.state.name }}</p>
		<hr/>
  </div>
</template>

<script>
import Task from './Task.vue'

export default {
  components: {
    Task
  },

	props: {
		demoProps: {
			// type of props
			type: Object,
			// default value if not has demoProps
			default: () => {
				return {}
			}
		},
		demoProps2: {
			// type of props
			type: String,
			// default value if not has demoProps
			default: 'default value'
		}
	},

	// có gái trị như state bên react
	data() {
		return {
			isWatch: '',
			// biến được theo dõi
			id: 'abc',
			name: 'Nguyen Tuan Anh',
			isShow: true,
			selected: false,
			tasks: [
				'choi game',
				'nghe nhac',
				'xem phim'
			]
		}
	},

	mounted() {
		// được gọi đầu tiên
		// thg dùng để fetch api
		console.log('mounted');
	},

	// methods of vue js
	// call func: this.aFunc()
	methods: {
		aFunc: function() {
			// to do something
			console.log('call function');
		}
	},

	// hàm theo dõi sự thay đổi của 1 data
	watch: {
		//  được gọi khi biến isWatch thay đổi
		isWatch: function(newVal, oldVal) {
			// to do something
			console.log(newVal);
			console.log(oldVal);
		}
	},

	// format data before render
	filter: {
		// format data function
		formatFunc: function(val) {
			return val
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.selected {
	color: red;
}
</style>
