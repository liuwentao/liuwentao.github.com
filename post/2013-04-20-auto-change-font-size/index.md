
字体的大小设定可以在开始的时候指定.但是有时候需要根据窗口或者文字的长短来指定.那么这个时候就需要用到时间Paint了.
继承与Control的控件都有这个事件.也可以override OnPaint函数.
主要考虑两个因素,宽度和高度.比方如果字体的长度小于一个比例,则增加字体大小.如果大于一个比例则减小字体.

高度也是同样的道理.控制在一个比例范围以内就可以了.

```csharp
        /// <summary>
        /// 标题重绘时候的处理
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void txtTitle_Paint(object sender, PaintEventArgs e)
        {
            var lbl = sender as Label;
            if (lbl == null)
            {
                return;
            }
            var size = MeasureStringWidth(lbl.Text, e.Graphics, lbl.Font);
            float diff = size.Width / lbl.Width;
            var font = lbl.Font;
            while ((diff > 0.6 || diff < 0.4))
            {

                font = new Font(font.Name, diff > 0.5 ? font.Size - 1 : font.Size + 1, font.Style);
                size = MeasureStringWidth(lbl.Text, e.Graphics, font);
                if (size.Height > lbl.Height)
                {
                    font = new Font(font.Name, diff > 0.5 ? font.Size + 1 : font.Size - 1, lbl.Font.Style);
                    break;
                }
                if (font.Size < 5)
                {
                    break;
                }
                diff = size.Width / lbl.Width;
            }
            lbl.Font = font;
        }
        /// <summary>
        /// 获得文字的高宽
        /// </summary>
        /// <param name="text">文字内容</param>
        /// <param name="graphic">绘画</param>
        /// <param name="font">字体</param>
        /// <returns>大小</returns>
        public static SizeF MeasureStringWidth(string text, Graphics graphic, Font font)
        {
            SizeF tmpSize = System.Windows.Forms.TextRenderer.MeasureText(text, font);
            return tmpSize;
        }
```