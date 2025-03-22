
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


#### 禁用 avatar头像

如何禁用？
**只需要在你启用的主题下的funcation.php文件，添加下面代码即刻生效！**

```js
// @date dill.2025年3月23日 在主题的 functions.php 中添加以下代码，禁用avatar头像，有效
add_filter( 'get_avatar', 'replace_gravatar_with_local', 1, 5 );
function replace_gravatar_with_local( $avatar, $id_or_email, $size, $default, $alt ) {
    // 直接返回本地默认头像（需提前上传到 /wp-content/uploads/local-avatar.png）
    return '<img src="'.content_url( '/wp-content/themes/twentytwentyfour/assets/images/localavatar.png' ).'" width="'.$size.'" height="'.$size.'" alt="'.$alt.'" class="avatar" />';
}

// 彻底禁用所有头像请求
add_filter( 'get_avatar_url', '__return_false' );

add_action( 'init', 'twentytwentyfour_pattern_categories' );
```



