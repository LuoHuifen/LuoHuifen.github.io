layout: post
tags: project python
date: 2016-9-05 22:10
thumbnail: /images/thumbnails/logo_rabbit.jpg 
title: ������������Ԥ������������ݷ���
published: true
excerpt: ����һƪ����д���Ѿ���ȥ�˴���꣬���������ò��ͼ�¼���Լ�����Ŀ��������βμ���ش����д����һ���Ŷ�Э������Ҫ�����ǿ�����ʵ��Ӧ�û����кܴ�ͬ�ġ����ڱ�����Ŀ����Ҫ�е����ݷ�����ְ�����������£�Time Series Decomposition, word embedding��
---
### ������� ###
���ǰ�����ص�һ������������������Ϻ��������50�����˸����Ļ�����Ϣ���������ʱ�䡢�����ĳ�ʼ���Ŵ������������Եȣ��Լ�����Щ������صĹ�ȥ6���µ��û����ż�¼�����û�����ʱ�䡢�û���Ϊ���ͣ����š����ء��ղأ���Ҫ�������Щ���ݣ�Ԥ����50�������ڽ�����2����ÿ��Ĳ�������

Ϊ�˽��������⣬����ͬʱ�����ݺ�ģ�������Ƕ����֡�һ�����ѽ���ģ�͵��С�һ�����ѽ��д���ʵ�֣��������**���ݷ���**��

### ���ݷ��� ###
�������ݲ�������
�����ȿ��ǵ��������ǣ�Ϻ�������ϸ������û���¼�����޴󣬶���������ֻ��50�����˵ĸ�����Ϣ�Լ���Լ35���û��Ĳ��ż�¼����Щ��������δ�������������ȡ�����ģ��ٷ�˵�����������ȡ�����Լ���Ӧ�ĸ�����Ȼ����Щ������ص��û���Ϊ��¼��ʷ����������������ڣ�**���˸����嵥֮�������ȡ����Ӧ���û���Ϊ��¼�������Ȼ�������������ص��û���¼��Ȼ��������������������������һ�����û���Ȼ
����ȡ�����Ƕ�����ѡ�������û���¼��**

�����һ����������Ļ���Ҳ���Ǳ������û���¼�����Ǵ������������ص��û���¼��������������ġ���ô�����û���¼�е��û�Ӧ��������ģ����ǵ�Ϻ�������Ӵ�������������Ǽ��������������ȡ��ͬһ���û��Ķ���û���¼�����ȽϺ��֣������д�����ͬһ���û���ͬһ�׸����ڲ�ͬʱ���ļ�¼�����������Ϊ�������ݵĻ�ù����������ģ�

1.�����ȡ50�����ˣ�Ȼ��õ���Щ���˵����и�����10278�ף���
2.�����ȡ35���û���Ȼ��õ���Щ�û���Ŀ��ʱ��ε�����ȡ�ĸ�����ص��û�������

��η��������ǽ���������Ԥ����������ķ�����������������Ԫ���ϣ�**����**��**����**��**�û�**��

### �����ղ�����ʱ�����зֽ� ###

Ϊ�˿��ٹ���baseline��ʼģ�͵����������������ۣ��������ȿ�������򵥵������Ҳ����ֱ�ӶԸ���ÿ��Ĳ��������н�ģ�������Ը������û����н�ģ��Ϊ�ˣ������ȶ�ÿ������ÿ�յĲ���������ʱ�����зֽ⣬��һ��ʱ�����зֽ�Ϊ `Trend  + Seasonal + residual` �����֣�**trend** ��ʾ���ֲ����������ƣ�**seasonal** ��ʾ���ֲ����������ڱ仯��**residual**���ܲ�������ȥtrend �� seasonal ֮��ʣ�µĲв����ټ������ӣ�

<div><img src="/images/ali-music-competition/Fig1.png" width="100%"></div>

��ͼ�Ǵ���2e14d32266ee6b4678595f8f50c369ac���ֵ��û�ÿ�ղ�����¼����ɫ��ʾ����������ɫ��ʾ����������ɫ��ʾ�ղ�����������7��Ϊ���ڶԲ���������ʱ�����зֽ⣬�õ���ͼ��

<div><img src="/images/ali-music-competition/Fig2.png" width="100%"></div>

���Կ������ø��ֳ���������ʱ�������˲������������⣬����ʱ��㶼��Ϊƽ�ȣ���ˣ��������û�и����¼����������ǹ��Ƹø��ֵĲ����������о��ұ仯��

������ͼ��ʾ���ø��ַ��������β�������������������������û������������Բ������������ڼ�����Ѹ���½���������ƽ�ȡ�

<div><img src="/images/ali-music-competition/Fig3.png" width="100%"></div>

<div><img src="/images/ali-music-competition/Fig4.png" width="100%"></div>

### ���ָ�����Ϣ�ռ� ###
��������ķ�����������ʶ�������ڸ��ֲ��������ԣ����û��ͻ���¼��ķ�����һ�㲻�ᷢ����ı仯�����һ����򵥵�Ԥ��ģ���ǽ����ֹ�ȥ6���²�������ƽ��ֵ��Ϊ����2���µĲ�����Ԥ�⣬��ʵ�ϣ�����һ���򵥵ķ���ȡ���˷ǳ������Ч������һ���棬���㲥������ΪĳЩ�¼������˴�ı仯��������ֶ����û���������Ҳ�����˲���������������ʱ�䡣������û���ṩ�������ص�������Ϣ��������Ǿ���������Ѱ���������صĸ������ݡ�

Ѱ�ҵķ�ʽ��Ҫ����������Ϣ����������ʱ�䡢�������ԡ������Ա�ƽ��������������������ʱ��㡣һ����˵��ƽ����������ĸ��ֽ�Ϊ������������С�ĸ������ΪС�ڣ��������������Ը�ע�ز�������ĸ��ֵ�Ԥ�⣬��������Ƚ�������������Щ�������ϡ����⣬��Ϊ�����������������ǵ�����Ҳ�����׷��֡�

��Ϊ���������ݽ���������������������Ҫ�ָ�id������ľ��庬�塣�������ݵ����Ի������Բ³�����������ʲô��


<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-slkj{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-kkwu{font-weight:bold;font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-gq9a{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-align:center}
.tg .tg-k9ij{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-align:center;vertical-align:top}
.tg .tg-m2jw{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-kkwu">����ID</th>
    <th class="tg-gq9a">0</th>
    <th class="tg-gq9a">1</th>
    <th class="tg-k9ij">2</th>
    <th class="tg-k9ij">3</th>
    <th class="tg-k9ij">4</th>
    <th class="tg-k9ij">100</th>
    <th class="tg-k9ij">11</th>
    <th class="tg-k9ij">14</th>
    <th class="tg-k9ij">12</th>
  </tr>
  <tr>
    <td class="tg-kkwu">��ʵֵ</td>
    <td class="tg-slkj"></td>
    <td class="tg-slkj">����</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw">Ӣ��</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw">����</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw"></td>
  </tr>
</table>

<p></p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-slkj{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-kkwu{font-weight:bold;font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-gq9a{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-align:center}
.tg .tg-k9ij{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-align:center;vertical-align:top}
.tg .tg-px6o{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-pztl{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-kkwu">�Ա�ID</th>
    <th class="tg-gq9a">1</th>
    <th class="tg-gq9a">2</th>
    <th class="tg-k9ij">3</th>
  </tr>
  <tr>
    <td class="tg-kkwu">��ʵֵ</td>
    <td class="tg-px6o">��</td>
    <td class="tg-slkj">Ů</td>
    <td class="tg-pztl">���</td>
  </tr>
</table>

<p></p>

�����������Բ�������ĸ����������²²⣬�����ｫ����������Ϊ�ղ���������1000�ף��������飬�����ĸ��ֲ����ࣩ

��50λ���ֹ�ȥ6���µ����и������ղ������ܺͻ��Ƴ�ͼ�������ǣ����������һ�����ݣ����������������&���ģ�ƾ����������������һ�¹��ڽϻ����ϣ�SHE�����߲���Ϊ���¸跢������һ���¸跢��������ЧӦ�Ǿ޴�ģ����ղ�����2000+ֱ��������20,000+�����棬����SHE��ר������ʱ���Ϻ�������ϵ�ר������ʱ����һ�µģ�����2016.05.20��һ���¸衶���������꡷��Ϊ��Ӱ����������������һʱ��

<div><img src="/images/ali-music-competition/Fig5.png" width="100%"></div>

ͬ���أ����Ǹ������&Ӣ�Ĳ²����ͼ����ΪBeatles�������������������ļ��죬����2016.05.18���ֲ�����������ԭ���п����ǡ����������ꡱ�����������棬���ݳ����Ŷ�����������hey, judy���������Ļ���ЧӦ��

<div><img src="/images/ali-music-competition/Fig6.png" width="100%"></div>

ͨ�����ַ�ʽ������ȷ���˽ӽ�10λ���ֵ���ݣ������ǶԲ���������������ֵ�ԭ�����˽�һ�����˽⡣������Ҫ���ǣ��ɴ����ǿ�������һ���µ�����������ĳ�յ�������������ĳ���ֵ����д������ų���ʱ�����ǿ����Ʋ�ø��ֻ�����ղ�����������Ϊ�ˣ���д��һ����������ԡ����֡�+�����ڡ�Ϊ�ؼ�����ȡ���ֵ�ÿ����������������û�в³���ݵĸ��֣�����Ĭ�ϸø���û�г��ֱ�ը�����š�



### �û���¼���� ###
��ĿǰΪֹ���Ҷ�û�д�΢�۲���ʹ���û��������ݡ������ǵ��û���¼���������ģ�����Ҵ�����û��ĽǶȽ��н�ģ�������һ������û�ÿ�յĲ�����¼������ͼ��ʾ��

<div><img src="/images/ali-music-competition/Fig7.png" width="100%"></div>

ͼ�к�����Ϊ���ڣ�������Ϊ����id�����ǽ�ͬһ�����ֵĸ�������������id����ɫ�����α�ʾ���أ���ɫԲȦ��ʾ���š����Կ�������λ�û�ֻ����λ���ֵĸ��������Ҷ�������֮��ʼ���š����⣬����̽�������ϵͣ�����һ�����������֮���û�����������ˡ�

<div><img src="/images/ali-music-competition/Fig8.png" width="100%"></div>


��λ�û���һ����̽������������ϲ���ĸ�����������������Ե�������Ҳ�᲻���صس������ʸ�����ͨ�������ͼʾ�����ǿ���֪����1�����غ�ĸ������û�һ������Եĳ�������2���û����ͬһ�����ֵĲ�ͬ����������Ȥ��


�ڷ��������û����û���¼ʱ����ͻȻ�������û�������¼���ı��������ԣ�����������������ȣ�

һ�׸�                               <==>        һ����

һ���û�ĳ��ʱ��Ĳ�����¼           <==>        һ������

һ���û������в�����¼               <==>        һƪ����

�������������֮�����й�����Ȼ���Դ�����о�������Ӧ�õ��û���Ϊ�������档��ʹ������ģ�Ͷ��û����о��࣬ʹ��word embedding�Ը������о��࣬�ȵȡ�

ͨ���������ȣ������Ƚ�ÿ�׸���ӳ�䵽һ�����ص�id��Ȼ���û�������¼����ʱ��˳������ת��Ϊ�ı���Ȼ�����ÿ�Դ��word embedding���룬����Щ�ı�Ϊ���룬���������embedding vector��Ϊ�˷����Ӿ��鿴������TSNE����ά���ݽ�ά��2ά�������Ϊ���������϶࣬���ɲ����ԣ��ҽ�����ӳ�䵽���֡��������ͼ��

<div><img src="/images/ali-music-competition/Fig10.png" width="100%"></div>



ͼ�в�ͬ�ķ��ű�Ǵ���ͬ�ĸ��֡����Կ�������Ȼ�ڼ��������embedding vectorʱ���ǲ�û��ʹ���κθ������йص���Ϣ����ͬһ�����ֵĸ���Ȼ�ܺõؾۼ���һ����˵��ͨ���û���¼�õ��ĸ���embeddingȷʵ�߱�ĳЩ������Ϣ������Ҳ��ӳ�˸��������û�ѡ���������Ҫ���ݡ���ͼ�����������м������־ۼ���һ����˵����ƾ������Ϣ�޷�������һ���ֵĸ�����

ͬ���ط�ʽ���ҽ�����ӳ�䵽�����Ա𣬵õ����½����

<div><img src="/images/ali-music-competition/Fig11.png" width="100%"></div>


��һ�ο��Կ������м䲿�����ֵ��Ժ�һЩ�ˡ�˵�������Ա�Ҳ���û��������Ҫѡ���׼��

������ǽ�����ӳ�䵽�������ԣ��õ����½��������ķ���ͬ�����ã�˵����������Ҳ���û�ѡ�����������֮һ��

<div><img src="/images/ali-music-competition/Fig12.png" width="100%"></div>

��Ȼ����������ĸ��֡��Ա����Զ��û�ѡ���������Ҫ���ǲ��Զ����ġ��ҵķ������������ݵ���ʽӡ֤����һ�������⣬������Ҫ���ǣ��������ǶԸ�������һ��ʸ�����Ķ������������ֱ����Է���ضԸ������о��ࡣͨ������ķ�����Ҳ����ȷ�ţ����־�������ĳЩ������������Ϣ��