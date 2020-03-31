# CustomScrollView 初入门

### CustomScrollView的作用

简单来说，就是把几个可以滑动的Widget组合成一个滑动的Widget

#### 最简单的使用场景

合并（不是混排）两个ListView内容

#### 实例

**使用SingleChildScrollView解决的布局**

```dart
Expanded(
    child: SingleChildScrollView(
      child: Column(
        children: <Widget>[
          ListView.builder(
            padding: EdgeInsets.all(0),
            shrinkWrap: true,
            physics: NeverScrollableScrollPhysics(),
            itemBuilder: adapter.itemBuilder,
            itemCount: adapter.itemCount,
          ),
          viewService.buildComponent('ticket_flow'),
        ],
      ),
    ),
  )
```

**将上面使用SingleChildScrollView的布局转换成使用CustomScrollView布局**

```dart
Expanded(
    child: CustomScrollView(
      slivers: <Widget>[
        SliverList(
          delegate: SliverChildBuilderDelegate(
            adapter.itemBuilder,
            childCount: adapter.itemCount,
          ),
        ),
        SliverToBoxAdapter(
          child: viewService.buildComponent('ticket_flow'),
        ),
      ],
    ),
  )
```

#### 建议

在`CustomScrollView`中，需要组合不滑动的布局时，可以使用`SliverToBoxAdapter`包裹布局

