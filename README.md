
![image](https://github.com/user-attachments/assets/8a0108f8-0e8c-49b4-829a-181b5b1e9a43)

---


# WordPress中国大陆访问加速优化方案

##   WordPress核心优化

### 代码层优化

#### 移除谷歌字体等境外资源依赖 

路径`wp-includes/script-loader.php` 

第一处，修改
源地址
`ajax.googleapis.com`
修改为
`ajax.lug.ustc.edu.cn` 

第二处，修改

```js
 /**
         * @date dill.2025年3月22日更换谷歌字体源
         */
		$open_sans_font_url = "https://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,300,400,600&subset=$subsets&display=fallback";
		$open_sans_font_url = "https://fonts.useso.com/css?family=Open+Sans:300italic,400italic,600italic,300,400,600&subset=$subsets&display=fallback";
```

#### 将js脚本修改成本地访问js
![image](https://github.com/user-attachments/assets/57553ead-b87b-4dbd-bf27-155079359bd2)





