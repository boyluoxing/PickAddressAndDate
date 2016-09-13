日期地址联动选择，选中item为红色，字体更大，item上下有边线
使用规则，以日期选择为例：
直接代码解释，我信你看的懂。

    //一般项目都是点击某个view来显示日期选择dialog，这里是点击一个Button btn来显示一个日期选择dialog
		btn.setOnClickListener(new OnClickListener() {
			@Override
			public void onClick(View v) {	//点击btn时，显示dialog
			  //step.1 实例一个ChangeBirthDialog  dialog，这个ChangeBirthDialog名字不规范，你可以按心情改
				ChangeBirthDialog mChangeBirthDialog = new ChangeBirthDialog(MainActivity.this);
				final Calendar calendar=Calendar.getInstance();
				//step.2 设置默认选中日期，这里设置的是当前时间的年月日
				mChangeBirthDialog.setDate(calendar.get(Calendar.YEAR), calendar.get(Calendar.MONTH)+1, calendar.get(Calendar.DATE));
				//step.3 显示dialog，这样你就可以滑动选择日期了
				mChangeBirthDialog.show();
				//step.4 给dialog设置回调接口，用于获取选中的日期
				mChangeBirthDialog.setBirthdayListener(new OnBirthListener() {
					@Override
					public void onClick(String year, String month, String day) {
						Toast.makeText(MainActivity.this,year + "-" + month + "-" + day,Toast.LENGTH_LONG).show();
					}
				});
			}
		});
如果，要修改效果，可以修改WheelView的draw方法，这个draw可不是override的draw而是自定义的一些draw方法。
