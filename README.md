# one-day-day
##1 <view class="wrap">
2 <view class="total" :class="{ select: true, active: item.id === sel }" v-for="(item,index) in tabs" :key="index"
3 @click="select(item)">
4 {{ item.label }}
5 </view>
6 </view>
