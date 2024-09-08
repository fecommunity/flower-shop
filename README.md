<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p>本文介绍了通过uniapp技术实现了一套栀子手作在线购物商城系统。包含首页、分类、我的等常用功能入口。</p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote --></blockquote>
<!-- /wp:quote -->

<!-- wp:image {"id":1024,"width":"575px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG350-2-768x1024.jpg" alt="" class="wp-image-1024" style="width:575px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:heading -->
<h2 class="wp-block-heading">一、功能演示</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>首页：包含了商品介绍，领劵中心和商品列表区域。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>商品分类：支持不同的商品分类和商品搜素。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>商品详情：包含了商品详细的描述信息，透出了分享、首页、客服等入口。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>我的：包含了账户的常见的个人操作信息，知乎此领劵，在线客服，钱包管理等入口。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>H5端在线体验地址：<a href="https://wx.gaoredu.com/">https://wx.gaoredu.com/</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>微信小程序：可以直接搜索“栀子手作”进入在线体验。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1026,"sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/flower.jpg" alt="" class="wp-image-1026"/></figure>
<!-- /wp:image -->

<!-- wp:heading -->
<h2 class="wp-block-heading">二、开发流程</h2>
<!-- /wp:heading -->

<!-- wp:heading -->
<h2 class="wp-block-heading">2.1 项目准备与搭建</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading">1. 环境搭建</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>首先，确保你已经安装了Node.js和HBuilderX，因为uniapp的项目可以通过HBuilderX来方便地创建和管理。安装HBuilderX后，在官网（<a href="https://www.dcloud.io/hbuilderx.html%EF%BC%89%E4%B8%8B%E8%BD%BD%E5%B9%B6%E5%AE%89%E8%A3%85%E3%80%82" target="_blank" rel="noreferrer noopener">https://www.dcloud.io/hbuilderx.html）下载并安装。</a></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading">2. 创建uniapp项目</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>启动HBuilderX，点击菜单栏中的“文件”→“新建”→“项目”，选择“uni-app”类型，输入项目名称（如“huahuaMall”），选择项目保存路径，点击“创建”按钮。项目创建成功后，你会看到一个基本的项目结构，包括<code>pages</code>、<code>static</code>、<code>components</code>等目录。</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2 class="wp-block-heading">2.2 首页设计</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>这里是栀子手作的小店的首页设计：</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1020,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG19-461x1024.jpg" alt="" class="wp-image-1020"/></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading">1. 页面布局</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>首页是商城的门户，通常包含轮播图、搜索框、热门商品列表等功能模块。</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul class="wp-block-list"><!-- wp:list-item -->
<li><strong>轮播图</strong>：使用<code>&lt;swiper></code>和<code>&lt;swiper-item></code>组件展示。</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li><strong>搜索框</strong>：自定义一个搜索组件，可以放置在<code>&lt;view class="header"></code>中。</li>
<!-- /wp:list-item -->

<!-- wp:list-item -->
<li><strong>商品列表</strong>：使用<code>&lt;view v-for="..."></code>循环遍历商品数据，每个商品使用<code>&lt;view class="product-item"></code>展示。</li>
<!-- /wp:list-item --></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading">2. 示例代码</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&lt;template>
  &lt;view class="container" :style="appThemeStyle">
    &lt;!-- 店铺页面组件 -->
    &lt;Page :items="items" />
    &lt;!-- 用户隐私保护提示（仅微信小程序） -->
    &lt;!-- #ifdef MP-WEIXIN -->
    &lt;PrivacyPopup :hideTabBar="true" />
    &lt;!-- #endif -->
  &lt;/view>
&lt;/template>

&lt;script>
  import { setCartTabBadge } from '@/core/app'
  import * as Api from '@/api/page'
  import Page from '@/components/page'
  import PrivacyPopup from '@/components/privacy-popup'

  const App = getApp()

  export default {
    components: {
      Page,
      PrivacyPopup
    },
    data() {
      return {
        // 页面参数
        options: {},
        // 页面属性
        page: {},
        // 页面元素
        items: &#91;]
      }
    },

    /**
     * 生命周期函数--监听页面加载
     */
    onLoad(options) {
      // 当前页面参数
      this.options = options
      // 加载页面数据
      this.getPageData()
    },

    /**
     * 生命周期函数--监听页面显示
     */
    onShow() {
      // 更新购物车角标
      setCartTabBadge()
    },

    methods: {

      /**
       * 加载页面数据
       * @param {Object} callback
       */
      getPageData(callback) {
        const app = this
        const pageId = app.options.pageId || 0
        Api.detail(pageId)
          .then(result => {
            // 设置页面数据
            const { data: { pageData } } = result
            app.page = pageData.page
            app.items = pageData.items
            // 设置顶部导航栏栏
            app.setPageBar()
          })
          .finally(() => callback &amp;&amp; callback())
      },

      /**
       * 设置顶部导航栏
       */
      setPageBar() {
        const { page } = this
        // 设置页面标题
        uni.setNavigationBarTitle({
          title: page.params.title
        })
        // 设置navbar标题、颜色
        uni.setNavigationBarColor({
          frontColor: page.style.titleTextColor === 'white' ? '#ffffff' : '#000000',
          backgroundColor: page.style.titleBackgroundColor
        })
      }

    },

    /**
     * 下拉刷新
     */
    onPullDownRefresh() {
      // 获取首页数据
      this.getPageData(() => {
        uni.stopPullDownRefresh()
      })
    },

    /**
     * 分享当前页面
     */
    onShareAppMessage() {
      const app = this
      const { page } = app
      return {
        title: page.params.shareTitle,
        path: "/pages/index/index?" + app.$getShareUrlParams()
      }
    },

    /**
     * 分享到朋友圈
     * 本接口为 Beta 版本，暂只在 Android 平台支持，详见分享到朋友圈 (Beta)
     * https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share-timeline.html
     */
    onShareTimeline() {
      const app = this
      const { page } = app
      return {
        title: page.params.shareTitle,
        path: "/pages/index/index?" + app.$getShareUrlParams()
      }
    }

  }
&lt;/script>

&lt;style lang="scss" scoped>
  .container {
    background: #fff;
  }
&lt;/style></code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2 class="wp-block-heading">2.3 分类页面设计</h2>
<!-- /wp:heading -->

<!-- wp:image {"id":1021,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG20-461x1024.jpg" alt="" class="wp-image-1021"/></figure>
<!-- /wp:image -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&lt;template>
  &lt;view class="container">
    &lt;!-- 搜索框 -->
    &lt;view class="search">
      &lt;search tips="搜索商品" @event="$navTo('pages/search/index')" />
    &lt;/view>

    &lt;!-- 一级分类 -->
    &lt;primary
      v-if="setting.style == PageCategoryStyleEnum.ONE_LEVEL_BIG.value || setting.style == PageCategoryStyleEnum.ONE_LEVEL_SMALL.value"
      :display="setting.style" :list="list" />

    &lt;!-- 二级分类 -->
    &lt;secondary v-if="setting.style == PageCategoryStyleEnum.TWO_LEVEL.value" :list="list" />

    &lt;!-- 分类+商品 -->
    &lt;commodity v-if="setting.style == PageCategoryStyleEnum.COMMODITY.value" ref="mescrollItem" :list="list" :setting="setting" />
  &lt;/view>
&lt;/template>

&lt;script>
  import MescrollCompMixin from '@/uni_modules/mescroll-uni/components/mescroll-uni/mixins/mescroll-comp'
  import { setCartTabBadge } from '@/core/app'
  import SettingKeyEnum from '@/common/enum/setting/Key'
  import { PageCategoryStyleEnum } from '@/common/enum/store/page/category'
  import SettingModel from '@/common/model/Setting'
  import * as CategoryApi from '@/api/category'
  import Search from '@/components/search'
  import Primary from './components/primary'
  import Secondary from './components/secondary'
  import Commodity from './components/commodity'

  // 最后一次刷新时间
  let lastRefreshTime;

  export default {
    components: {
      Search,
      Primary,
      Secondary,
      Commodity
    },
    mixins: &#91;MescrollCompMixin],
    data() {
      return {
        // 枚举类
        PageCategoryStyleEnum,
        // 分类列表
        list: &#91;],
        // 分类模板设置
        setting: {},
        // 正在加载中
        isLoading: true
      }
    },

    /**
     * 生命周期函数--监听页面加载
     */
    onLoad() {
      // 加载页面数据
      this.onRefreshPage()
    },

    /**
     * 生命周期函数--监听页面显示
     */
    onShow() {
      // 每间隔5分钟自动刷新一次页面数据
      const curTime = new Date().getTime()
      if ((curTime - lastRefreshTime) > 5 * 60 * 1000) {
        this.onRefreshPage()
      }
    },

    methods: {

      // 刷新页面
      onRefreshPage() {
        // 记录刷新时间
        lastRefreshTime = new Date().getTime()
        // 获取页面数据
        this.getPageData()
        // 更新购物车角标
        setCartTabBadge()
      },

      // 获取页面数据
      getPageData() {
        const app = this
        app.isLoading = true
        Promise.all(&#91;
            // 获取分类模板设置
            // 优化建议: 可以将此处的false改为true 启用缓存
            SettingModel.data(false),
            // 获取分类列表
            CategoryApi.list()
          ])
          .then(result => {
            // 初始化分类模板设置
            app.initSetting(result&#91;0])
            // 初始化分类列表数据
            app.initCategory(result&#91;1])
          })
          .finally(() => app.isLoading = false)
      },

      /**
       * 初始化分类模板设置
       * @param {Object} result
       */
      initSetting(setting) {
        this.setting = setting&#91;SettingKeyEnum.PAGE_CATEGORY_TEMPLATE.value]
      },

      /**
       * 初始化分类列表数据
       * @param {Object} result
       */
      initCategory(result) {
        this.list = result.data.list
      },

    },

    /**
     * 设置分享内容
     */
    onShareAppMessage() {
      const app = this
      return {
        title: _this.templet.shareTitle,
        path: '/pages/category/index?' + app.$getShareUrlParams()
      }
    },

    /**
     * 分享到朋友圈
     * 本接口为 Beta 版本，暂只在 Android 平台支持，详见分享到朋友圈 (Beta)
     * https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share-timeline.html
     */
    onShareTimeline() {
      const app = this
      return {
        title: _this.templet.shareTitle,
        path: '/pages/category/index?' + app.$getShareUrlParams()
      }
    }

  }
&lt;/script>

&lt;style>
  page {
    background: #fff;
  }
&lt;/style>
&lt;style lang="scss" scoped>
  // 搜索框
  .search {
    position: fixed;
    top: var(--window-top);
    left: var(--window-left);
    right: var(--window-right);
    z-index: 9;
  }
&lt;/style></code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2 class="wp-block-heading">2.4 商品详情页面设计</h2>
<!-- /wp:heading -->

<!-- wp:image {"id":1025,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG21-1-461x1024.jpg" alt="" class="wp-image-1025"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>相关代码演示：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&lt;template>
	&lt;view v-show="!isLoading" class="container" :style="appThemeStyle">
		&lt;!-- 商品图片轮播 -->
		&lt;SlideImage v-if="!isLoading" :video="goods.video" :videoCover="goods.videoCover"
			:images="goods.goods_images" />

		&lt;!-- 商品信息 -->
		&lt;view v-if="!isLoading" class="goods-info m-top20">
			&lt;!-- 价格、销量 -->
			&lt;view class="info-item info-item__top dis-flex flex-x-between flex-y-end">
				&lt;view class="block-left dis-flex flex-y-center">
					&lt;!-- 商品售价 -->
					&lt;text class="floor-price__samll">￥&lt;/text>
					&lt;text class="floor-price">{{ goods.goods_price_min }}&lt;/text>
					&lt;!-- 会员价标签 -->
					&lt;view v-if="goods.is_user_grade" class="user-grade">
						&lt;text>会员价&lt;/text>
					&lt;/view>
					&lt;!-- 划线价 -->
					&lt;text v-if="goods.line_price_min > 0" class="original-price">￥{{ goods.line_price_min }}&lt;/text>
				&lt;/view>
				&lt;view class="block-right dis-flex">
					&lt;!-- 销量 -->
					&lt;view class="goods-sales">
						&lt;text>已售{{ goods.goods_sales }}件&lt;/text>
					&lt;/view>
				&lt;/view>
			&lt;/view>
			&lt;!-- 标题、分享 -->
			&lt;view class="info-item info-item__name dis-flex flex-y-center">
				&lt;view class="goods-name flex-box">
					&lt;text class="twoline-hide">{{ goods.goods_name }}&lt;/text>
				&lt;/view>
				&lt;view class="goods-share__line">&lt;/view>
				&lt;view class="goods-share">
					&lt;button class="share-btn dis-flex flex-dir-column" @click="onShowShareSheet()">
						&lt;text class="share__icon iconfont icon-fenxiang">&lt;/text>
						&lt;text class="f-24">分享&lt;/text>
					&lt;/button>
				&lt;/view>
			&lt;/view>
			&lt;!-- 商品卖点 -->
			&lt;view v-if="goods.selling_point" class="info-item info-item_selling-point">
				&lt;text>{{ goods.selling_point }}&lt;/text>
			&lt;/view>
		&lt;/view>

		&lt;!-- 选择商品规格 -->
		&lt;view v-if="goods.spec_type == 20" class="goods-choice m-top20 b-f" @click="onShowSkuPopup(1)">
			&lt;view class="spec-list">
				&lt;view class="flex-box">
					&lt;text class="col-8">选择：&lt;/text>
					&lt;text class="spec-name" v-for="(item, index) in goods.specList"
						:key="index">{{ item.spec_name }}&lt;/text>
				&lt;/view>
				&lt;view class="f-26 col-9 t-r">
					&lt;text class="iconfont icon-arrow-right">&lt;/text>
				&lt;/view>
			&lt;/view>
		&lt;/view>

		&lt;!-- 商品服务 -->
		&lt;Service v-if="!isLoading" :goods-id="goodsId" />

		&lt;!-- 商品SKU弹窗 -->
		&lt;SkuPopup v-if="!isLoading" v-model="showSkuPopup" :skuMode="skuMode" :goods="goods" @addCart="onAddCart" />

		&lt;!-- 商品评价 -->
		&lt;Comment v-if="!isLoading" :goods-id="goodsId" :limit="2" />

		&lt;!-- 商品描述 -->
		&lt;view v-if="!isLoading" class="goods-content m-top20">
			&lt;view class="item-title b-f">
				&lt;text>商品描述&lt;/text>
			&lt;/view>
			&lt;view v-if="goods.content != ''" class="goods-content__detail b-f">
				&lt;mp-html :content="goods.content" />
			&lt;/view>
		&lt;/view>

		&lt;!-- 底部选项卡 -->
		&lt;view class="footer-fixed">
			&lt;view class="footer-container">
				&lt;!-- 导航图标 -->
				&lt;view class="foo-item-fast">
					&lt;!-- 首页 -->
					&lt;view class="fast-item fast-item--home" @click="onTargetHome">
						&lt;view class="fast-icon">
							&lt;text class="iconfont icon-shouye">&lt;/text>
						&lt;/view>
						&lt;view class="fast-text">
							&lt;text>首页&lt;/text>
						&lt;/view>
					&lt;/view>
					&lt;!-- 客服 -->
					&lt;customer-btn v-if="isShowCustomerBtn" :showCard="true" :cardTitle="goods.goods_name"
						:cardImage="goods.goods_image">
						&lt;view class="fast-item">
							&lt;view class="fast-icon">
								&lt;text class="iconfont icon-kefu1">&lt;/text>
							&lt;/view>
							&lt;view class="fast-text">
								&lt;text>客服&lt;/text>
							&lt;/view>
						&lt;/view>
					&lt;/customer-btn>
					&lt;!-- 购物车 -->
					&lt;!-- &lt;view class="fast-item fast-item--cart" @click="onTargetCart">
            &lt;view v-if="cartTotal > 0" class="fast-badge fast-badge--fixed">{{ cartTotal > 99 ? '99+' : cartTotal }}
            &lt;/view>
            &lt;view class="fast-icon">
              &lt;text class="iconfont icon-gouwuche">&lt;/text>
            &lt;/view>
            &lt;view class="fast-text">
              &lt;text>购物车&lt;/text>
            &lt;/view>
          &lt;/view> -->
				&lt;/view>
				&lt;!-- 操作按钮 -->
				&lt;view class="foo-item-btn">
					&lt;view class="btn-wrapper">
						&lt;!-- &lt;view v-if="isEnableCart" class="btn-item btn-item-deputy" @click="onShowSkuPopup(2)">
              &lt;text>加入购物车&lt;/text>
            &lt;/view> -->
						&lt;view class="btn-item btn-item-main" @click="onShowSkuPopup(3)">
							&lt;text>更多详情&lt;/text>
						&lt;/view>
					&lt;/view>
				&lt;/view>
			&lt;/view>
		&lt;/view>

		&lt;!-- 快捷导航 -->
		&lt;!-- &lt;shortcut bottom="120rpx" /> -->

		&lt;!-- 分享菜单 -->
		&lt;share-sheet v-model="showShareSheet" :shareTitle="goods.goods_name" :shareImageUrl="goods.goods_image" />

		&lt;!-- 二维码扫码 -->
		&lt;u-modal v-model="showQrModal" :title="温馨提示">
			&lt;view class="qrcode">
				&lt;text>下单请长按二维码➕微信&lt;/text>
				&lt;image src="../../static/qrcode.jpg" mode="widthFix" :show-menu-by-longpress="true"/>
			&lt;/view>
		&lt;/u-modal>
	&lt;/view>
&lt;/template>

&lt;script>
	import {
		getSceneData
	} from '@/core/app'
	import * as GoodsApi from '@/api/goods'
	import * as CartApi from '@/api/cart'
	import SettingModel from '@/common/model/Setting'
	import {
		GoodsTypeEnum
	} from '@/common/enum/goods'
	import ShareSheet from '@/components/share-sheet'
	import CustomerBtn from '@/components/customer-btn'
	import SlideImage from './components/SlideImage'
	import SkuPopup from './components/SkuPopup'
	import Comment from './components/Comment'
	import Service from './components/Service'

	export default {
		components: {
			ShareSheet,
			CustomerBtn,
			SlideImage,
			SkuPopup,
			Comment,
			Service
		},
		data() {
			return {
				// 正在加载
				isLoading: true,
				// 当前商品ID
				goodsId: null,
				// 商品详情
				goods: {},
				// 购物车总数量
				cartTotal: 0,
				// 显示/隐藏SKU弹窗
				showSkuPopup: false,
				// 模式 1:都显示 2:只显示购物车 3:只显示立即购买
				skuMode: 1,
				// 显示/隐藏分享菜单
				showShareSheet: false,
				// 是否支持加入购物车
				isEnableCart: false,
				// 是否显示在线客服按钮
				isShowCustomerBtn: false,
				// 是否展示QrModal
				showQrModal: false,
			}
		},

		/**
		 * 生命周期函数--监听页面加载
		 */
		async onLoad(options) {
			// 记录query参数
			this.onRecordQuery(options)
			// 加载页面数据
			this.onRefreshPage()
			// 是否显示在线客服按钮
			this.isShowCustomerBtn = await SettingModel.isShowCustomerBtn()
		},

		methods: {

			// 记录query参数
			onRecordQuery(query) {
				const scene = getSceneData(query)
				this.goodsId = query.goodsId ? parseInt(query.goodsId) : parseInt(scene.gid)
			},

			// 刷新页面数据
			onRefreshPage() {
				const app = this
				app.isLoading = true
				Promise.all(&#91;app.getGoodsDetail(), app.getCartTotal()])
					.finally(() => app.isLoading = false)
			},

			// 获取商品信息
			getGoodsDetail() {
				const app = this
				return new Promise((resolve, reject) => {
					GoodsApi.detail(app.goodsId)
						.then(result => {
							app.goods = result.data.detail
							if (app.goods.goods_type == GoodsTypeEnum.PHYSICAL.value) {
								app.isEnableCart = true
							}
							resolve(result)
						})
						.catch(reject)
				})
			},

			// 获取购物车总数量
			getCartTotal() {
				const app = this
				return new Promise((resolve, reject) => {
					CartApi.total()
						.then(result => {
							app.cartTotal = result.data.cartTotal
							resolve(result)
						})
						.catch(reject)
				})
			},

			// 更新购物车数量
			onAddCart(total) {
				this.cartTotal = total
			},

			/**
			 * 显示/隐藏SKU弹窗
			 * @param {skuMode} 模式 1:都显示 2:只显示购物车 3:只显示立即购买
			 */
			onShowSkuPopup(skuMode = 1) {
				// 下单请联系客服
				this.showQrModal = true;
				// uni.showModal({
				// 	title: '温馨提示',
				// 	content: '下单请联系客服或➕微信：zzsz68'
				// });
				// WARNING：如下临时注释
				// const app = this
				// if (app.isEnableCart) {
				//   app.skuMode = skuMode
				// } else {
				//   app.skuMode = 3
				// }
				// app.showSkuPopup = !app.showSkuPopup
			},

			// 显示隐藏分享菜单
			onShowShareSheet() {
				this.showShareSheet = !this.showShareSheet
			},

			// 跳转到首页
			onTargetHome(e) {
				this.$navTo('pages/index/index')
			},

			// 跳转到购物车页
			onTargetCart() {
				this.$navTo('pages/cart/index')
			},

		},

		/**
		 * 分享当前页面
		 */
		onShareAppMessage() {
			const app = this
			// 构建页面参数
			const params = app.$getShareUrlParams({
				goodsId: app.goodsId,
			})
			return {
				title: app.goods.goods_name,
				path: `/pages/goods/detail?${params}`
			}
		},

		/**
		 * 分享到朋友圈
		 * 本接口为 Beta 版本，暂只在 Android 平台支持，详见分享到朋友圈 (Beta)
		 * https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share-timeline.html
		 */
		onShareTimeline() {
			const app = this
			// 构建页面参数
			const params = app.$getShareUrlParams({
				goodsId: app.goodsId,
			})
			return {
				title: app.goods.goods_name,
				path: `/pages/goods/detail?${params}`
			}
		}
	}
&lt;/script>

&lt;style>
	page {
		background: #fafafa;
	}
&lt;/style>
&lt;style lang="scss" scoped>
	@import "./detail.scss";
&lt;/style></code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2 class="wp-block-heading">2.4 我的页面设计</h2>
<!-- /wp:heading -->

<!-- wp:image {"id":1023,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG22-461x1024.jpg" alt="" class="wp-image-1023"/></figure>
<!-- /wp:image -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:code -->
<pre class="wp-block-code"><code>&lt;template>
  &lt;view v-if="!isFirstload" class="container" :style="appThemeStyle">
    &lt;!-- 页面头部 -->
    &lt;view class="main-header" :style="{ height: platform == 'H5' ? '260rpx' : '320rpx', paddingTop: platform == 'H5' ? '0' : '80rpx' }">
      &lt;image class="bg-image" src="/static/background/user-header2.png" mode="scaleToFill">&lt;/image>
      &lt;!-- 用户信息 -->
      &lt;view v-if="isLogin" class="user-info">
        &lt;view class="user-avatar" @click="handlePersonal()">
          &lt;avatar-image :url="userInfo.avatar_url" :width="100" />
        &lt;/view>
        &lt;view class="user-content">
          &lt;!-- 会员昵称 -->
          &lt;view class="nick-name oneline-hide" @click="handlePersonal()">{{ userInfo.nick_name }}&lt;/view>
          &lt;!-- 会员等级 -->
          &lt;view v-if="$checkModule('user-grade') &amp;&amp; userInfo.grade_id > 0 &amp;&amp; userInfo.grade" class="user-grade">
            &lt;view class="user-grade_icon">
              &lt;image class="image"
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAA0lBMVEUAAAD/tjL/tzH/uDP/uC7/tjH/tzH/tzL/tTH+tTL+tjP/tDD/tTD+tzD/tjL/szD/uDH/tjL/tjL+tjD/tjT/szb/tzL/tTL+uTH+tjL/tjL/tjL/tTT/tjL/tjL+tjH/uTL/vDD/tjL/tjH/tzL9uS//tTL/nBr/sS7/tjH/ujL/szD/uTv+rzf/tzL+tzH+vDP+uzL+tjP+ry7+tDL9ki/7szf/sEX/tTL/tjL+tjL/tTH/tTT/tzH/tzL/tjP/sTX/uTP/wzX+rTn/vDX9vC8m8ckhAAAAOXRSTlMAlnAMB/vjxKWGMh0S6drMiVxPRkEY9PLy0ru0sKagmo5+dGtgVCMgBP716eXWyMGxqJGRe2o5KSmFNjaYAAABP0lEQVQ4y8XS13KDMBAF0AWDDe4t7r3ETu9lVxJgJ/n/X8rKAzHG5TE+Twz3zki7I/g/KXdghIbGJewrU4yzn08Ebgl6TuZzzuOC6W5es3HX6qsSz3NFShRU0MpucytDmOSpu3yULx3CA9RD1HjVedc0jSjqm6ZzhUjDsFDQhSp/OKj5GQvg0+ZCOixsbtDLAeTTOm/yGi8GyIphIVsgH737FEDV44LJa88IRKK/SetrwT9G/GUIr6vXjoy4GXn7+RboVXnghuSjaoGecwQxL2su3CwAKlO+QFoqxI4FMctHQhQd2OhxTu184jWUlI+rMTBTn1/IQcJHQ6GQdZ7pWiDaNdhTt330efISeiqYwQEzQpTlsURJLhzkEmpCPsERfeIUVyXr6MNuIyp5uziW6xURtt7hhGwzmMNJExfO4Bd9X0ZPqAxdNwAAAABJRU5ErkJggg==">
              &lt;/image>
            &lt;/view>
            &lt;view class="user-grade_name">
              &lt;text>{{ userInfo.grade.name }}&lt;/text>
            &lt;/view>
          &lt;/view>
          &lt;!-- 会员无等级时显示手机号 -->
          &lt;view v-else class="mobile">{{ userInfo.mobile }}&lt;/view>
        &lt;/view>
      &lt;/view>
      &lt;!-- 未登录 -->
      &lt;view v-else class="user-info" @click="handleLogin">
        &lt;view class="user-avatar">
          &lt;avatar-image :width="100" />
        &lt;/view>
        &lt;view class="user-content">
          &lt;view class="nick-name">未登录&lt;/view>
          &lt;view class="login-tips">点击登录账号&lt;/view>
        &lt;/view>
      &lt;/view>
    &lt;/view>

    &lt;!-- 绑定手机号 -->
    &lt;!-- &lt;view v-if="isLogin &amp;&amp; !userInfo.mobile &amp;&amp; setting&#91;SettingKeyEnum.REGISTER.value].isManualBind" class="my-mobile"
      @click="handleBindMobile()">
      &lt;view class="info">点击绑定手机号，确保账户安全&lt;/view>
      &lt;view class="btn-bind">去绑定&lt;/view>
    &lt;/view> -->

    &lt;!-- 我的钱包 -->
    &lt;view v-if="$checkModules(&#91;'market-recharge', 'market-points', 'market-coupon'])" class="my-asset">
      &lt;view class="asset-left flex-box dis-flex flex-x-around">
        &lt;view v-if="$checkModule('market-recharge')" class="asset-left-item" style="max-width: 200rpx;" @click="onTargetWallet">
          &lt;view class="item-value dis-flex flex-x-center">
            &lt;text class="oneline-hide">{{ isLogin ? assets.balance : '--' }}&lt;/text>
          &lt;/view>
          &lt;view class="item-name dis-flex flex-x-center">
            &lt;text>账户余额&lt;/text>
          &lt;/view>
        &lt;/view>
        &lt;view v-if="$checkModule('market-points')" class="asset-left-item" @click="onTargetPoints">
          &lt;view class="item-value dis-flex flex-x-center">
            &lt;text class="oneline-hide">{{ isLogin ? assets.points : '--' }}&lt;/text>
          &lt;/view>
          &lt;view class="item-name dis-flex flex-x-center">
            &lt;text>{{ setting&#91;SettingKeyEnum.POINTS.value].points_name }}&lt;/text>
          &lt;/view>
        &lt;/view>
        &lt;view v-if="$checkModule('market-coupon')" class="asset-left-item" @click="onTargetMyCoupon">
          &lt;view class="item-value dis-flex flex-x-center">
            &lt;text class="oneline-hide">{{ isLogin ? assets.coupon : '--' }}&lt;/text>
          &lt;/view>
          &lt;view class="item-name dis-flex flex-x-center">
            &lt;text>优惠券&lt;/text>
          &lt;/view>
        &lt;/view>
      &lt;/view>
      &lt;view v-if="$checkModule('market-recharge')" class="asset-right">
        &lt;view class="asset-right-item" @click="onTargetWallet">
          &lt;view class="item-icon dis-flex flex-x-center">
            &lt;text class="iconfont icon-qianbao">&lt;/text>
          &lt;/view>
          &lt;view class="item-name dis-flex flex-x-center">
            &lt;text>我的钱包&lt;/text>
          &lt;/view>
        &lt;/view>
      &lt;/view>
    &lt;/view>

    &lt;!-- 绑定手机号 (第2种样式) -->
    &lt;!-- &lt;view class="my-mobile2" @click="handleBindMobile()">
      &lt;view class="info">点击绑定手机号，确保账户安全&lt;/view>
      &lt;view class="btn-bind">去绑定&lt;/view>
    &lt;/view> -->

    &lt;!-- 订单操作 -->
    &lt;!-- &lt;view class="order-navbar">
      &lt;view class="order-navbar-item" v-for="(item, index) in orderNavbar" :key="index" @click="onTargetOrder(item)">
        &lt;view class="item-icon">
          &lt;text class="iconfont" :class="&#91;`icon-${item.icon}`]">&lt;/text>
        &lt;/view>
        &lt;view class="item-name">{{ item.name }}&lt;/view>
        &lt;view class="item-badge" v-if="item.count &amp;&amp; item.count > 0">
          &lt;text v-if="item.count &lt;= 99" class="text">{{ item.count }}&lt;/text>
          &lt;text v-else class="text">99+&lt;/text>
        &lt;/view>
      &lt;/view>
    &lt;/view> -->

    &lt;!-- 我的服务 -->
    &lt;view class="my-service">
      &lt;view class="service-title">我的服务&lt;/view>
      &lt;view class="service-content clearfix">
        &lt;block v-for="(item, index) in service" :key="index">
          &lt;view v-if="item.type == 'link' &amp;&amp; item.enabled" class="service-item" @click="handleService(item)">
            &lt;view class="item-icon">
              &lt;text class="iconfont" :class="&#91;`icon-${item.icon}`]">&lt;/text>
            &lt;/view>
            &lt;view class="item-name">{{ item.name }}&lt;/view>
            &lt;view class="item-badge" v-if="item.count &amp;&amp; item.count > 0">
              &lt;text v-if="item.count &lt;= 99" class="text">{{ item.count }}&lt;/text>
              &lt;text v-else class="text">99+&lt;/text>
            &lt;/view>
          &lt;/view>
          &lt;!-- 在线客服 -->
          &lt;view v-if="item.type == 'contact' &amp;&amp; item.enabled" class="service-item">
            &lt;customer-btn>
              &lt;view class="item-icon">
                &lt;text class="iconfont" :class="&#91;`icon-${item.icon}`]">&lt;/text>
              &lt;/view>
              &lt;view class="item-name">{{ item.name }}&lt;/view>
            &lt;/customer-btn>
          &lt;/view>
        &lt;/block>
      &lt;/view>
    &lt;/view>

    &lt;!-- 退出登录 -->
    &lt;view v-if="isLogin" class="my-logout">
      &lt;view class="logout-btn" @click="handleLogout()">
        &lt;text>退出登录&lt;/text>
      &lt;/view>
    &lt;/view>

  &lt;/view>
&lt;/template>

&lt;script>
  import store from '@/store'
  import { inArray } from '@/utils/util'
  import AvatarImage from '@/components/avatar-image'
  import CustomerBtn from '@/components/customer-btn'
  import { setCartTabBadge } from '@/core/app'
  import SettingKeyEnum from '@/common/enum/setting/Key'
  import StoreModel from '@/common/model/Store'
  import SettingModel from '@/common/model/Setting'
  import * as UserApi from '@/api/user'
  import * as OrderApi from '@/api/order'
  import { checkLogin, filterModules } from '@/core/app'

  // 订单操作
  const orderNavbar = &#91;
    { id: 'all', name: '全部订单', icon: 'qpdingdan' },
    { id: 'payment', name: '待支付', icon: 'daifukuan', count: 0 },
    { id: 'delivery', name: '待发货', icon: 'daifahuo', count: 0 },
    { id: 'received', name: '待收货', icon: 'daishouhuo', count: 0 },
  ]

  /**
   * 我的服务
   * id: 标识; name: 标题名称; icon: 图标; type 类型(link和button); url: 跳转的链接
   */
  const service = &#91;
    // { id: 'address', name: '收货地址', icon: 'shouhuodizhi', type: 'link', url: 'pages/address/index' },
    { id: 'coupon', name: '领券中心', icon: 'lingquan', type: 'link', url: 'pages/coupon/index', moduleKey: 'market-coupon' },
    { id: 'myCoupon', name: '优惠券', icon: 'youhuiquan', type: 'link', url: 'pages/my-coupon/index', moduleKey: 'market-coupon' },
    // { id: 'refund', name: '退换/售后', icon: 'shouhou', type: 'link', url: 'pages/refund/index', count: 0 },
    { id: 'contact', name: '在线客服', icon: 'kefu', type: 'contact' },
    { id: 'points', name: '我的积分', icon: 'jifen', type: 'link', url: 'pages/points/log', moduleKey: 'market-points' },
    // { id: 'orderCenter', name: '订单中心', icon: 'order-c', type: 'link', url: 'pages/order/center' },
    // { id: 'help', name: '我的帮助', icon: 'bangzhu', type: 'link', url: 'pages/help/index', moduleKey: 'content-help' },
  ]

  export default {
    components: {
      AvatarImage,
      CustomerBtn
    },
    data() {
      return {
        inArray,
        // 枚举类
        SettingKeyEnum,
        // 正在加载
        isLoading: true,
        // 首次加载
        isFirstload: true,
        // 是否已登录
        isLogin: false,
        // 系统设置
        setting: {},
        // 当前用户信息
        userInfo: {},
        // 账户资产
        assets: { balance: '--', points: '--', coupon: '--' },
        // 我的服务
        service,
        // 订单操作
        orderNavbar,
        // 当前用户待处理的订单数量
        todoCounts: { payment: 0, deliver: 0, received: 0 }
      }
    },

    /**
     * 生命周期函数--监听页面显示
     */
    onLoad(options) {},

    /**
     * 生命周期函数--监听页面显示
     */
    onShow(options) {
      this.onRefreshPage()
    },

    methods: {

      // 刷新页面
      onRefreshPage() {
        // 更新购物车角标
        setCartTabBadge()
        // 判断是否已登录
        this.isLogin = checkLogin()
        // 获取页面数据
        this.getPageData()
      },

      // 获取页面数据
      getPageData(callback) {
        const app = this
        app.isLoading = true
        Promise.all(&#91;app.getSetting(), app.getUserInfo(), app.getUserAssets(), app.getTodoCounts()])
          .then(result => {
            app.isFirstload = false
            // 初始化我的服务数据
            app.initService()
            // 初始化订单操作数据
            app.initOrderTabbar()
            // 执行回调函数
            callback &amp;&amp; callback()
          })
          .catch(err => console.log('catch', err))
          .finally(() => app.isLoading = false)
      },

      // 初始化我的服务数据
      async initService() {
        const app = this
        const isShowCustomerBtn = await SettingModel.isShowCustomerBtn()
        const newService = &#91;]
        service.forEach(item => {
          // 默认开启
          item.enabled = true
          // 我的积分
          if (item.id === 'points') {
            item.name = '我的' + app.setting&#91;SettingKeyEnum.POINTS.value].points_name
          }
          // 企业微信客服
          if (item.id === 'contact' &amp;&amp; !isShowCustomerBtn) {
            item.enabled = false
          }
          // 数据角标
          if (item.count != undefined) {
            item.count = app.todoCounts&#91;item.id]
          }
          newService.push(item)
        })
        app.service = filterModules(newService)
      },

      // 初始化订单操作数据
      initOrderTabbar() {
        const app = this
        const newOrderNavbar = &#91;]
        orderNavbar.forEach(item => {
          if (item.count != undefined) {
            item.count = app.todoCounts&#91;item.id]
          }
          newOrderNavbar.push(item)
        })
        app.orderNavbar = newOrderNavbar
      },

      // 获取商城设置
      getSetting() {
        const app = this
        return new Promise((resolve, reject) => {
          SettingModel.data()
            .then(setting => {
              app.setting = setting
              resolve(setting)
            })
            .catch(reject)
        })
      },

      // 获取当前用户信息
      getUserInfo() {
        const app = this
        return new Promise((resolve, reject) => {
          !app.isLogin ? resolve(null) : UserApi.info({}, { load: app.isFirstload })
            .then(result => {
              app.userInfo = result.data.userInfo
              resolve(app.userInfo)
            })
            .catch(err => {
              if (err.result &amp;&amp; err.result.status == 401) {
                app.isLogin = false
                resolve(null)
              } else {
                reject(err)
              }
            })
        })
      },

      // 获取账户资产
      getUserAssets() {
        const app = this
        return new Promise((resolve, reject) => {
          !app.isLogin ? resolve(null) : UserApi.assets({}, { load: app.isFirstload })
            .then(result => {
              app.assets = result.data.assets
              resolve(app.assets)
            })
            .catch(err => {
              if (err.result &amp;&amp; err.result.status == 401) {
                app.isLogin = false
                resolve(null)
              } else {
                reject(err)
              }
            })
        })
      },

      // 获取当前用户待处理的订单数量
      getTodoCounts() {
        const app = this
        return new Promise((resolve, reject) => {
          !app.isLogin ? resolve(null) : OrderApi.todoCounts({}, { load: app.isFirstload })
            .then(result => {
              app.todoCounts = result.data.counts
              resolve(app.todoCounts)
            })
            .catch(err => {
              if (err.result &amp;&amp; err.result.status == 401) {
                app.isLogin = false
                resolve(null)
              } else {
                reject(err)
              }
            })
        })
      },

      // 跳转到登录页
      handleLogin() {
        !this.isLogin &amp;&amp; this.$navTo('pages/login/index')
      },

      // 跳转到绑定手机号页面
      handleBindMobile() {
        this.$navTo('pages/user/bind/index')
      },

      // 跳转到修改个人信息页
      handlePersonal() {
        this.$navTo('pages/user/personal/index')
      },

      // 退出登录
      handleLogout() {
        const app = this
        uni.showModal({
          title: '友情提示',
          content: '您确定要退出登录吗?',
          success(res) {
            if (res.confirm) {
              store.dispatch('Logout', {})
                .then(result => app.onRefreshPage())
            }
          }
        })
      },

      // 跳转到钱包页面
      onTargetWallet() {
        this.$navTo('pages/wallet/index')
      },

      // 跳转到订单页
      onTargetOrder(item) {
        this.$navTo('pages/order/index', { dataType: item.id })
      },

      // 跳转到我的积分页面
      onTargetPoints() {
        this.$navTo('pages/points/log')
      },

      // 跳转到我的优惠券页
      onTargetMyCoupon() {
        this.$navTo('pages/my-coupon/index')
      },

      // 跳转到服务页面
      handleService({ url }) {
        this.$navTo(url)
      }

    },

    /**
     * 下拉刷新
     */
    onPullDownRefresh() {
      // 获取首页数据
      this.getPageData(() => {
        uni.stopPullDownRefresh()
      })
    },


  }
&lt;/script>

&lt;style lang="scss" scoped>
  .container {
    padding-bottom: 60rpx;
  }

  // 页面头部
  .main-header {
    // background-color: #FBF7EF;
    position: relative;
    width: 100%;
    height: 280rpx;
    background-size: 100% 100%;
    overflow: hidden;
    display: flex;
    align-items: center;
    padding-left: 30rpx;

    .bg-image {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
    }

    .user-info {
      display: flex;
      height: 100rpx;
      z-index: 1;

      .user-content {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-left: 30rpx;
        color: #c59a46;

        .nick-name {
          font-size: 34rpx;
          font-weight: bold;
          max-width: 300rpx;
        }

        .mobile {
          margin-top: 15rpx;
          font-size: 28rpx;
        }

        .user-grade {
          align-self: baseline;
          display: flex;
          align-items: center;
          background: #3c3c3c;
          margin-top: 12rpx;
          border-radius: 10rpx;
          padding: 4rpx 12rpx;

          .user-grade_icon .image {
            display: block;
            width: 32rpx;
            height: 32rpx;
          }

          .user-grade_name {
            margin-left: 5rpx;
            font-size: 26rpx;
            color: #EEE0C3;
          }

        }

        .login-tips {
          margin-top: 12rpx;
          font-size: 30rpx;
        }

      }
    }
  }

  // 角标组件
  .item-badge {
    position: absolute;
    top: 0;
    right: 55rpx;
    // background: $main-bg;
    background: #fa2209;
    color: #fff;
    border-radius: 100%;
    min-width: 38rpx;
    height: 38rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rpx;
    font-size: 24rpx;
  }

  // 我的钱包
  .my-asset {
    display: flex;
    background: #fff;
    padding: 40rpx 0;

    .asset-right {
      width: 200rpx;
      border-left: 1rpx solid #eee;
    }

    .asset-right-item {
      text-align: center;
      color: #545454;

      .item-icon {
        font-size: 44rpx;
      }

      .item-name {
        margin-top: 14rpx;
        font-size: 28rpx;
      }

    }

    .asset-left-item {
      max-width: 183rpx;
      text-align: center;
      color: #666;
      padding: 0 16rpx;

      .item-value {
        font-size: 34rpx;
        color: $main-bg;
      }

      .item-name {
        margin-top: 14rpx;
        font-size: 28rpx;
      }

    }

  }

  // 订单操作
  .order-navbar {
    display: flex;
    margin: 20rpx auto 20rpx auto;
    padding: 20rpx 0 26rpx 0;
    width: 94%;
    box-shadow: 0 1rpx 5rpx 0px rgba(0, 0, 0, 0.05);
    font-size: 30rpx;
    border-radius: 5rpx;
    background: #fff;

    &amp;-item {
      position: relative;
      width: 25%;

      .item-icon {
        text-align: center;
        margin: 0 auto;
        padding: 10rpx 0;
        color: #545454;
        font-size: 44rpx;
      }

      .item-name {
        font-size: 28rpx;
        color: #545454;
        text-align: center;
        margin-right: 10rpx;
      }

    }
  }

  // 我的服务
  .my-service {
    margin: 22rpx auto 22rpx auto;
    padding: 22rpx 0;
    width: 94%;
    box-shadow: 0 1rpx 5rpx 0px rgba(0, 0, 0, 0.05);
    border-radius: 5rpx;
    background: #fff;

    .service-title {
      padding-left: 24rpx;
      margin-bottom: 20rpx;
      font-size: 30rpx;
    }

    .service-content {

      margin-bottom: -20rpx;

      .service-item {
        position: relative;
        width: 25%;
        float: left;
        margin-bottom: 30rpx;

        .item-icon {
          text-align: center;
          margin: 0 auto;
          padding: 14rpx 0;
          color: $main-bg;
          font-size: 44rpx;
        }

        .item-name {
          font-size: 28rpx;
          color: #545454;
          text-align: center;
        }

      }
    }
  }

  // 退出登录
  .my-logout {
    display: flex;
    justify-content: center;
    margin-top: 50rpx;

    .logout-btn {
      width: 60%;
      margin: 0 auto;
      font-size: 28rpx;
      color: #616161;
      border-radius: 20rpx;
      border: 1px solid #dcdcdc;
      padding: 16rpx 0;
      text-align: center;
    }
  }

  // 绑定手机号 样式1
  .my-mobile {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16rpx 40rpx;
    background: #FCEBD1;

    .info {
      color: #cd8c0c;
      font-size: 28rpx;
    }

    .btn-bind {
      padding: 8rpx 24rpx;
      background-color: #EAB766;
      color: #fff;
      border-radius: 30rpx;
      font-size: 26rpx;
      text-align: center;
    }
  }

  // 绑定手机号 样式2
  .my-mobile2 {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 20rpx auto 20rpx auto;
    padding: 12rpx 40rpx;
    width: 94%;
    box-shadow: 0 1rpx 5rpx 0px rgba(0, 0, 0, 0.05);
    font-size: 30rpx;
    border-radius: 5rpx;
    background: #fff;

    .info {
      // color: #cd8c0c;
      font-size: 26rpx;
    }

    .btn-bind {
      padding: 8rpx 24rpx;
      background-color: #EAB766;
      color: #fff;
      border-radius: 30rpx;
      font-size: 26rpx;
      text-align: center;
    }
  }
&lt;/style></code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2 class="wp-block-heading">三、项目总结</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>由于篇幅原因，更多信息和源码可直接联系本人微信（red_tea_v2），代码和服务部署可以提供技术支持，其他问题可直接在文章下面评论。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1027,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="https://www.gaoredu.com/wp-content/uploads/2024/08/WechatIMG23-751x1024.jpg" alt="" class="wp-image-1027"/></figure>
<!-- /wp:image --></blockquote>
<!-- /wp:quote -->
