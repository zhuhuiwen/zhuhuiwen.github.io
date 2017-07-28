---
layout: post
title:  "echarts基本使用"
categories: 图表类
tags:  echarts
---

## ehcarts柱状图使用 ##
>ECharts，纯Javascript图表库，基于Canvas，底层依赖ZRender，
>商业产品通用图表库，提供直观，生动，可交互，可个性化定制的数据可视化图表，支持折线图（区域图）、柱状图（条状图）、散点图（气泡图）、K线图、饼图（环形图）、雷达图（填充雷达图）、和弦图、力导向布局图、地图（内置世界地图、中国及全国34个省市自治区地理数据），同时支持任意维度的堆积和多图表混合展现。




### 基本配置 ###
- 页面显示区

		
		<div id="main" style="width: 600px;height: 400px;"></div>
	
- 引入依赖的包

		
		<script src="./js/echarts.min.js"></script>
		<!-- 使用jq的ajax -->
		<script src="./js/jquery-1.8.3.min.js"></script>
    	
- 配置数据

		
		<script>
		// 获取显示区域
		var mainId = document.getElementById("main");
		// 初始化echarts实例
		var myChart = echarts.init(mainId);
		// 进行图标基本配置
		myChart.setOption({
		    title: {
		        text: '2017上半年销量'
		    },
		    tooltip: {},
		    legend: {
		        data:['销量']
		    },
		    xAxis: {
		        data: []
		    },
		    yAxis: {},
		    series: [{
		        name: '销量',
		        type: 'bar',
		        data: []
		    }]
		});
		// 获取json数据
        $.ajax({
        	type : "get",
        	url : "http://127.0.0.1:8020/demo/json/data.json",
        	dataType:"json",
        	beforeSend : function() {
        		// 未显示数据之前进行显示loading
        		myChart.showLoading();
        	},
        	success: function(result) {
        		myChart.hideLoading();
	      		myChart.setOption({
			        xAxis: {
			            data: result.categories
			        },
			        series: [{
			            // 根据名字对应到相应的系列
			            name: '销量',
			            data: result.data
			        }]
			    });
        	}
        })
	</script>

- json数据

		{
	   		 "categories": ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"],
	    	"data":  [15, 20, 36, 10, 10, 20]
		}

### 细节配置 ###

- 主要是配置字体显示

			<script>
						var mainId = document.getElementById("main");
						var myChart = echarts.init(mainId);
						myChart.setOption({
							    title: {
							        text: '2017上半年产值',
							        subtext: '数据来google'
							    },
							    tooltip: {
							        trigger: 'axis',
							        axisPointer: {
							            type: 'shadow'
							        }
							    },
							    legend: {
							        data: ['2017年']
							    },
							    grid: {
							        left: '3%',
							        right: '4%',
							        bottom: '3%',
							        containLabel: true
							    },
							    xAxis: {
							        type: 'value',
							        boundaryGap: [0, 0.01],
							        // 配置x轴的label的字体颜色和大小
							        axisLabel: {
				                        show: true,
				                        textStyle: {
				                            color: '#000',
				                            fontSize: 14
				                        }
				                    }
							    },
							    yAxis: {
							        type: 'category',
							        data: ['companyname10','companyname9','companyname8','companyname7','companyname6','companyname5','companyname4','companyname3','companyname2','companyname1'],
							        // 配置y轴的字体颜色和大小
							        axisLabel: {
				                        show: true,
				                        textStyle: {
				                            color: '#000',
				                            fontSize: 14
				                        }
				                    }
							    },
							    series: [
							        {
							            name: '2017年',
							            type: 'bar',
							            data: [5872.46, 2262.80, 2012.24, 1193.40, 962.80, 793.40,598.84,193.60,91.14,53.23],
							            // 配置柱状图上的显示data
				               			 itemStyle: {
											normal: {
												color:'#6be6c1',
												label: {
													show: true,
													position: 'right',
													textStyle: {
														color: '#000',
														fontSize: 14
													},
													formatter:function(params){
														if(params.value==0){
															return '';
														}else{
															return params.value;
														}
													}
												}
											}
										}
							        }
							   	 ]
								}
							);
					</script>
