# PopupWindow

 private PopupWindowList mPopupWindowList;
    private void showPopWindows(View view, boolean self, ChatBean chatBeanDB){
        List<String> dataList = new ArrayList<>();
        dataList.add("复制");
        if (mPopupWindowList == null){
            mPopupWindowList = new PopupWindowList(view.getContext());
        }
        mPopupWindowList.setAnchorView(view);
        mPopupWindowList.setItemData(dataList);
        mPopupWindowList.setModal(true);
        mPopupWindowList.show();
        mPopupWindowList.setOnItemClickListener((parent, v, position, id) -> {
            LogUtils.e( "click position="+position);
            mPopupWindowList.hide();
            //获取当前选择的值
            Adapter adpter=parent.getAdapter();
            String str=(String)adpter.getItem(position);//拿到当前数据值并强转   adpter.getItem(i)即为当前数据对象
            if (str.equals("复制")) {
              //逻辑代码
            }
        });
    }
  +
    int[] location = new int[2];
    view.getLocationOnScreen(location);
    float OldListY = (float) location[1];
    float OldListX = (float) location[0];
    tipViewBuilder = new TipView.Builder(context, mChatView, (int) OldListX + view.getWidth() / 2, (int) OldListY + view.getHeight());
    tipViewBuilder.addItem(new TipItem("复制"));
    tipViewBuilder.setOnItemClickListener(new TipView.OnItemClickListener() {
        @Override
        public void onItemClick(String str, final int position) {
            if ("复制".equals(str)) {
              // 复制
            }
        }

        @Override
        public void dismiss() {
        
        }
    });
    tipView = tipViewBuilder.create();
