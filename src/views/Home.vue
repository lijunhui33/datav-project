<template>
	<div class="home">
		<dv-full-screen-container style="height: 100vh;">
			<!-- <dv-loading>Loading...</dv-loading> -->
			<!-- <dv-border-box-8 :reverse="true">dv-border-box-8</dv-border-box-8>
		 -->
			<dv-decoration-11 style="height: 10vh;color: white;font-size: 40px;width: 98%;margin: 10px auto;">招聘会实时统计平台</dv-decoration-11>
			<!-- <dv-digital-flop :config="config1" style="width:200px;height:50px;color: white;" />
		  -->
			<div class="gw">
				<div class="list">
					<div class="num">{{ formatter(3698) }}</div>
					<div class="title">招聘企业</div>
				</div>

				<div class="list">
					<div class="num">{{ formatter(3111698) }}</div>
					<div class="title">岗位数</div>
				</div>
				<div class="list">
					<div class="num">{{ formatter(3111698) }}</div>
					<div class="title">职位数</div>
				</div>
				<div class="list">
					<div class="num">{{ formatter(3111698) }}</div>
					<div class="title">报名数</div>
				</div>
				<div class="list">
					<div class="num">{{ formatter(3111698) }}</div>
					<div class="title">进场人数</div>
				</div>
			</div>
			<!-- <dv-border-box-8 :reverse="true" style="height: 60vh;">dv-border-box-8</dv-border-box-8> -->
			<div class="bottom">
				<div class="list">
					<dv-border-box-1>
						<div class="title1">企业分布前十</div>
						<dv-capsule-chart :config="companyConfig" style="width:95%;margin-left: 2.5%;height: 36vh;" />
						<div class="title2">企业规模分布</div>
						<div style="100%;height: 25vh;display: flex;">
							<dv-active-ring-chart :config="gmConfig" style="width:60%;margin-left: 2.5%;height: 25vh;" />
							<div style="">
								<div  v-for="item in gmConfig.data" style="display: flex;">
									<div style="width: 30px;height: 20px;margin-bottom: 10px;border-radius: 4px;"
									:style="{background:item.color}"
									></div>
									<div style="padding-left: 10px;" :style="{color:item.color}">{{item.name}}</div>
								</div>
								
							</div>
						</div>
					</dv-border-box-1>
				</div>
				<div class="list2">
					<!-- <dv-decoration-5 style="width:100%;height:40px;"></dv-decoration-5> -->
					<div style="width: 100%;text-align: center;padding: 20px 0;font-size: 24px;">现场招聘实时信息滚动</div>
					<dv-scroll-board :config="lb" style="width:100%;height:15vh;margin-bottom: 5vh;" />
					<div style="height: 35vh;display: flex;align-items: center;width: 100%;margin-top: 20px;">
						<div style="width: 50%;">
							<div style="text-align: center;width: 100%;">岗位招聘学历分布</div>
							<dv-conical-column-chart :config="educationConfig" style="width: 80%;height: 35vh;" />
						</div>
						<div style="width: 50%;display: flex;flex-direction: row-reverse;flex-direction: column;">
							<div style="text-align: center;width: 100%;">企业薪资分布</div>
							<dv-conical-column-chart :config="companyXz" style="width: 100%;height: 35vh;" />
						</div>
					</div>
				</div>
				<div class="list"><dv-border-box-1>
				<div class="title1">求职者学历分布</div>
				<dv-capsule-chart :config="qzzConfig" style="width:95%;margin-left: 2.5%;height: 36vh;" />
				<div class="title2">求职意向</div>
				<div style="100%;height: 25vh;display: flex;">
					<dv-active-ring-chart :config="gmConfig" style="width:60%;margin-left: 2.5%;height: 25vh;" />
					<div style="">
						<div  v-for="item in qzzyxConfig.data" style="display: flex;">
							<div style="width: 30px;height: 20px;margin-bottom: 10px;border-radius: 4px;"
							:style="{background:item.color}"
							></div>
							<div style="padding-left: 10px;" :style="{color:item.color}">{{item.name}}</div>
						</div>
						
					</div>
				</div>
				
				</dv-border-box-1></div>
			</div>
		</dv-full-screen-container>
	</div>
</template>

<script>
// @ is an alias to /src
function formatter(number) {
	const numbers = number
		.toString()
		.split('')
		.reverse();
	const segs = [];

	while (numbers.length) segs.push(numbers.splice(0, 3).join(''));

	return segs
		.join(',')
		.split('')
		.reverse()
		.join('');
}

import echarts from 'echarts';
export default {
	name: 'Home',
	components: {},
	data() {
		return {
			educationConfig:{
				showValue: true,
				data: [
					{
						name:'初中及以下',
						value:30
					},
				    {
				      name: '高中',
				      value: 40
				    },
				    {
				      name: '大专',
				      value: 120
				    },{
						name: '本科',
						value: 120
					},{
						name: '硕士',
						value: 120
					},{
						name: '博士',
						value: 120
					}
				  ],
				  img: [
				   
				  ]
			},
			companyXz:{
				showValue: true,
				data: [
					{
						name:'4k以下',
						value:300
					},
				    {
				      name: '4-5K',
				      value: 40
				    },
				    {
				      name: '5-10K',
				      value: 120
				    },{
						name: '10K以上',
						value: 120
					}
				  ],
				  img: [
				   
				  ]
			},
			lb:{
				  data: [
				    ['张三签到入场', '张三签到入场2', '行张三签到入场列3'],
				    ['行2列1', '行2列2', '行2列3'],
				    ['行3列1', '行3列2', '行3列3'],
				    ['行4列1', '行4列2', '行4列3'],
				    ['行5列1', '行5列2', '行5列3'],
				    ['行6列1', '行6列2', '行6列3'],
				    ['行7列1', '行7列2', '行7列3'],
				    ['行8列1', '行8列2', '行8列3'],
				    ['行9列1', '行9列2', '行9列3'],
				    ['行10列1', '行10列2', '行10列3']
				  ],
				  // index: true,
				  // columnWidth: [50],
				  align: ['center'],
				  carousel: 'page',
				  oddRowBGC:'rgba(0,0,0,0)',
				  evenRowBGC:'rgba(0,0,0,0)'
			},
			red: 'red',
			formatter,
			gmConfig:{
				radius: '40%',
				  activeRadius: '45%',
				  lineWidth:12,
				  data: [
				    {
				      name: '1000以上',
				      value: 55,
					  color:'#36a1d9'
				    },
				    {
				      name: '200-1000',
				      value: 120,
					  color:'#32c5e9'
				    },
				    {
				      name: '100-200',
				      value: 78,
					  color:'#68e0e3'
				    },
				    {
				      name: '20-100',
				      value: 66,
					  color:'#9ee6b8'
				    },
				    {
				      name: '10-20',
				      value: 80,
					  color:'#ffdb5d'
				    }
				  ],
				  digitalFlopStyle: {
				    fontSize: 20
				  }
			},
			companyConfig: {
				data: [
					{
						name: '食品',
						value: 167
					},
					{
						name: '保鲜',
						value: 123
					},
					{
						name: '金融',
						value: 98
					},
					{
						name: '计算机',
						value: 75
					},
					{
						name: '自媒体',
						value: 66
					},
					{
						name: '餐饮',
						value: 66
					},
					{
						name: '自媒体1',
						value: 66
					},
					{
						name: '餐饮f',
						value: 66
					},
					{
						name: '自媒体4',
						value: 66
					},
					{
						name: '餐饮5',
						value: 66
					}
				],
				unit: '单位',
				showValue: true
			},
			qzzConfig:{
				data: [
					{
						name: '初中及以下',
						value: 10
					},
					{
						name: '高中',
						value: 123
					},
					{
						name: '大专',
						value: 98
					},
					{
						name: '本科',
						value: 75
					},
					{
						name: '硕士',
						value: 66
					},
					{
						name: '博士',
						value: 6
					},
					
				],
				unit: '人数',
				showValue: true
			},
			qzzyxConfig:{
				radius: '40%',
				  activeRadius: '45%',
				  lineWidth:12,
				  data: [
				    {
				      name: '金融',
				      value: 55,
					  color:'#36a1d9'
				    },
				    {
				      name: '销售',
				      value: 120,
					  color:'#32c5e9'
				    },
				    {
				      name: '电信',
				      value: 78,
					  color:'#68e0e3'
				    },
				    {
				      name: '会计',
				      value: 66,
					  color:'#9ee6b8'
				    },
				    {
				      name: '计算机',
				      value: 80,
					  color:'#ffdb5d'
				    }
				  ],
				  digitalFlopStyle: {
				    fontSize: 20
				  }
			},
		};
	}
};
</script>

<style lang="scss">
@import './home.scss';
</style>
