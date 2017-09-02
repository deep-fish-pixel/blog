# redux性能问题分析
1. reducers 可以嵌套，但reducer树越深，性能在初始化会越慢，因每一次嵌套，使用combineReducers都会重新触发初始化
2. 只要有dispatch，就会触发reducer树递归处理每一个reducer数据。
3. 然后触发所有connect的使用mapStateToProps的组件状态比较，注意是所有，有变化则打标记shouldUpdate为true
4. 最后每一次组件有更新，每个connect组件打标记的同时，都会触发根组件的setState更新

以上2，3，4在用户操作时，对性能的影响会更明显

