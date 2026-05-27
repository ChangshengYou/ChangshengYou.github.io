# 游昌盛主页修改与归档说明

本仓库由 `dingzhuwen/dingzhuwen.github.io` 克隆后改造，当前未上传 GitHub。完整原始信息归档保存在 `docs/you_changsheng_profile_archive.md`。

## 文件对应关系

- `_config.yml`: 站点标题、侧边栏姓名、邮箱、单位、地点、头像、未来 GitHub Pages URL。
- `_data/navigation.yml`: 顶部导航。当前包含 Publications、Awards、Services、Teaching、Group、Photos、News。
- `_pages/about.md`: 首页，包含基本信息、招聘、研究方向、简介、新闻、精选奖项、教育与经历。
- `_pages/news.md`: 新闻与 Call for Papers。
- `_pages/group.md`: 团队成员。新增人员时按 PI、Postdoctoral Researchers、Ph.D. Students、Master Students、Undergraduate Students、Visiting Students 分区追加。
- `_pages/publications.md`: 论文与专利主页面。当前从归档文件生成，按专题分组。
- `_pages/awards.md`: 完整奖项列表。
- `_pages/services.md`: 编辑、客座编辑、学术职务、Workshop、TPC、审稿服务。
- `_pages/teaching.md`: 教学信息。
- `_pages/photos.md`: 照片页占位，已删除文鼎柱原照片内容，后续可加入游昌盛课题组照片。
- `css/customized-stylesheet.css`: 团队页样式、论文专题图片槽位样式。
- `_data/site_content.yml`: 结构化资料索引，尤其记录论文专题图片槽位。
- `images/research/`: 预留给论文专题展示图。

## 论文专题图片接口

每个论文专题标题前都有一个隐藏槽位，例如：

```html
<div class="topic-image-slot" data-topic="near-field-communications-survey-tutorial" data-image=""></div>
```

后续添加图片时推荐两步：

1. 将图片放入 `images/research/`，例如 `images/research/near-field-survey.jpg`。
2. 在对应槽位中加入图片标签，并把 `data-image` 填成同一路径：

```html
<div class="topic-image-slot" data-topic="near-field-communications-survey-tutorial" data-image="{{ base_path }}/images/research/near-field-survey.jpg">
  <img src="{{ base_path }}/images/research/near-field-survey.jpg" alt="Near-field communications">
</div>
```

`data-image` 为空时该槽位不会显示，因此当前页面不会出现空白图片框。

## 后续常见修改

- 添加新成员：改 `_pages/group.md`，若有照片则放入 `images/` 或 `images/group/`，并把当前文字列表改成带照片的 `group-member` 块。项目页部署在 `/cys` 下时，图片路径建议写成 `{{ base_path }}/images/group/name.jpg`。
- 添加新论文：改 `_pages/publications.md`，在对应专题末尾追加编号；若新增专题，同时在 `_data/site_content.yml` 的 `publication_topic_image_slots` 里补一个 key。
- 修改首页新闻：改 `_pages/about.md` 首页精选新闻，同时在 `_pages/news.md` 保留完整新闻。
- 修改奖项：完整列表改 `_pages/awards.md`，首页只保留精选奖项。
- 修改服务：改 `_pages/services.md`。
- 修改头像：优先下载头像到 `images/`，再把 `_config.yml` 的 `author.avatar` 从远程 URL 改成本地文件名。
