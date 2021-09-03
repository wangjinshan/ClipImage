# 裁剪图片工具说明

### 入口:


```
let controller = ClipImageBrowserController(image: UIImage(named: "1")!, direction: .up)
controller.delegate = self
present(controller, animated: true, completion: nil)
```

### 出口

```
extension ViewController: ClipImageBrowserProtocol {
    func clickSureButton(controller: ClipImageBrowserController, clipImage: UIImage, clipImageRect: CGRect) {
        let temp = UIImageView(image: clipImage)
        temp.frame = CGRect(x: 10, y: 50, width: clipImageRect.width, height: clipImageRect.width)
        view.addSubview(temp)
        DispatchQueue.main.asyncAfter(wallDeadline: .now() + 3) {
            temp.removeFromSuperview()
        }
    }
}
```

#### TODO: 
1 自动监听屏幕旋转
2 支持放到手势的另一个文件裁剪


