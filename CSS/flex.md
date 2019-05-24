��ҳ���֣�layout����CSS��һ���ص�Ӧ�á�



���ֵĴ�ͳ������������ں�״ģ�ͣ����� display���� + position���� + float���ԡ���������Щ���Ⲽ�ַǳ������㣬���磬��ֱ���оͲ�����ʵ�֡�



2009�꣬W3C�����һ���µķ�����-Flex���֣����Լ�㡢��������Ӧʽ��ʵ�ָ���ҳ�沼�֡�Ŀǰ�����Ѿ��õ��������������֧�֣�����ζ�ţ����ھ��ܺܰ�ȫ��ʹ������ܡ�



Flex���ֽ���Ϊδ�����ֵ���ѡ���������Ľ���Flex���ֵ��﷨��

����������Ҫ�ο���������ƪ���£�A Complete Guide to Flexbox �� A Visual Guide to CSS3 Flexbox Properties��

һ��Flex������ʲô��
Flex��Flexible Box����д����Ϊ�����Բ��֡�������Ϊ��״ģ���ṩ��������ԡ�

�κ�һ������������ָ��ΪFlex���֡�

.box{
  display: flex;
}
����Ԫ��Ҳ����ʹ��Flex���֡�

.box{
  display: inline-flex;
}
Webkit�ں˵���������������-webkitǰ׺��

.box{
  display: -webkit-flex; /* Safari */
  display: flex;
}
ע�⣬��ΪFlex�����Ժ���Ԫ�ص�float��clear��vertical-align���Խ�ʧЧ��

������������
����Flex���ֵ�Ԫ�أ���ΪFlex������flex container������ơ�������������������Ԫ���Զ���Ϊ������Ա����ΪFlex��Ŀ��flex item������ơ���Ŀ����



����Ĭ�ϴ��������᣺ˮƽ�����ᣨmain axis���ʹ�ֱ�Ľ����ᣨcross axis��������Ŀ�ʼλ�ã���߿�Ľ���㣩����main start������λ�ý���main end��������Ŀ�ʼλ�ý���cross start������λ�ý���cross end��

��ĿĬ�����������С�������Ŀռ�ݵ�����ռ����main size��ռ�ݵĽ�����ռ����cross size��

��������������
����6�����������������ϡ�

flex-direction
flex-wrap
flex-flow
justify-content
align-items
align-content
3.1 flex-direction����
flex-direction���Ծ�������ķ��򣨼���Ŀ�����з��򣩡�

.box {
  flex-direction: row | row-reverse | column | column-reverse;
}


��������4��ֵ��

row��Ĭ��ֵ��������Ϊˮƽ�����������ˡ�
row-reverse������Ϊˮƽ����������Ҷˡ�
column������Ϊ��ֱ������������ء�
column-reverse������Ϊ��ֱ������������ء�
3.2 flex-wrap����
Ĭ������£���Ŀ������һ���ߣ��ֳơ����ߡ����ϡ�flex-wrap���Զ��壬���һ�������Ų��£���λ��С�



.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
������ȡ����ֵ��

��1��nowrap��Ĭ�ϣ��������С�



��2��wrap�����У���һ�����Ϸ���



��3��wrap-reverse�����У���һ�����·���



3.3 flex-flow
flex-flow������flex-direction���Ժ�flex-wrap���Եļ�д��ʽ��Ĭ��ֵΪrow nowrap��

.box {
  flex-flow: <flex-direction> <flex-wrap>;
}
3.4 justify-content����
justify-content���Զ�������Ŀ�������ϵĶ��뷽ʽ��

.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}


������ȡ5��ֵ��������뷽ʽ����ķ����йء������������Ϊ�����ҡ�

flex-start��Ĭ��ֵ���������
flex-end���Ҷ���
center�� ����
space-between�����˶��룬��Ŀ֮��ļ������ȡ�
space-around��ÿ����Ŀ����ļ����ȡ����ԣ���Ŀ֮��ļ������Ŀ��߿�ļ����һ����
3.5 align-items����
align-items���Զ�����Ŀ�ڽ���������ζ��롣

.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}


������ȡ5��ֵ������Ķ��뷽ʽ�뽻����ķ����йأ�������轻������ϵ��¡�

flex-start��������������롣
flex-end����������յ���롣
center����������е���롣
baseline: ��Ŀ�ĵ�һ�����ֵĻ��߶��롣
stretch��Ĭ��ֵ���������Ŀδ���ø߶Ȼ���Ϊauto����ռ�����������ĸ߶ȡ�
3.6 align-content����
align-content���Զ����˶�����ߵĶ��뷽ʽ�������Ŀֻ��һ�����ߣ������Բ������á�

.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}


�����Կ���ȡ6��ֵ��

flex-start���뽻����������롣
flex-end���뽻������յ���롣
center���뽻������е���롣
space-between���뽻�������˶��룬����֮��ļ��ƽ���ֲ���
space-around��ÿ����������ļ������ȡ����ԣ�����֮��ļ����������߿�ļ����һ����
stretch��Ĭ��ֵ��������ռ�����������ᡣ
�ġ���Ŀ������
����6��������������Ŀ�ϡ�

order
flex-grow
flex-shrink
flex-basis
flex
align-self
4.1 order����
order���Զ�����Ŀ������˳����ֵԽС������Խ��ǰ��Ĭ��Ϊ0��

.item {
  order: <integer>;
}


4.2 flex-grow����
flex-grow���Զ�����Ŀ�ķŴ������Ĭ��Ϊ0�����������ʣ��ռ䣬Ҳ���Ŵ�

.item {
  flex-grow: <number>; /* default 0 */
}


���������Ŀ��flex-grow���Զ�Ϊ1�������ǽ��ȷ�ʣ��ռ䣨����еĻ��������һ����Ŀ��flex-grow����Ϊ2��������Ŀ��Ϊ1����ǰ��ռ�ݵ�ʣ��ռ佫���������һ����

4.3 flex-shrink����
flex-shrink���Զ�������Ŀ����С������Ĭ��Ϊ1��������ռ䲻�㣬����Ŀ����С��

.item {
  flex-shrink: <number>; /* default 1 */
}


���������Ŀ��flex-shrink���Զ�Ϊ1�����ռ䲻��ʱ�������ȱ�����С�����һ����Ŀ��flex-shrink����Ϊ0��������Ŀ��Ϊ1����ռ䲻��ʱ��ǰ�߲���С��

��ֵ�Ը�������Ч��