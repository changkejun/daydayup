<html><body><h2 id="dbdesignTtl">6.1 【設問】受発注（3/3）</h2>


<h3>6.1.3 その他の詳細な属性の見直し</h3>
<h4 class="caption">例題7 受注ヘッダの受注属性を見直す</h4>
<div class="section">
<p class="txt">まず、業務の現状と要望事項を説明します。それを把握した上で、続く問題に答えなさい。</p>
<p class="txt">商品を発注した顧客が出荷先とは限らないことがわかりました。<br>
受注した商品の出荷先情報は受注先情報とは別に管理する必要があります。</p>
<!--/section--></div>

<div class="section">
<h5 class="quiz-title">Ｑ&nbsp;問題</h5>
<p class="txt">上記のような要件を満たすために必要な変更をER図に加えてください。</p>
<!--/section--></div>

<div class="section">
<h5 class="answer-title">Ｈ&nbsp;ヒント</h5>
<p class="txt">値引きの単位は受注単位、受注明細単位の両方で起きる可能性があるため、「受注」エンティティ、「受注明細」スーパータイプエンティティに値引きに必要な属性を追加します。<br>
値引きは受注明細の種類には関係ないため、サブタイプではなく、スーパータイプに追加します。</p>
<!--/section--></div>

<div class="section">
<h5 class="answer-title">Ａ&nbsp;解答</h5>
<!--/section--></div>

<div class="commandBox">
<div class="command">
<table width="100%">
<tr><td colspan="2" style="border:none;"><strong>受注</strong></td><td colspan="2" style="border:none;">：属性追加</td></tr>
<tr><td style="width:20px;">*</td><td style="width:150px;">受注注文番号</td><td style="width:80px;">&nbsp;</td><td style="width:200px;">&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>客先注文番号</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注日付</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注顧客コード</td><td>（FK1）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>出荷先顧客コード</td><td>（FK2）&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注社員コード</td><td>（FK3）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>値引き承認社員コード</td><td>（FK4）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注部門コード</td><td>（FK5）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き承認フラグ</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き非承認理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>値引き詳細番号</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>消費税額</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>税抜受注金額合計</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>納入希望日</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>摘要</td><td>&nbsp;</td><td>&nbsp;</td></tr>
</table>
</div>
</div><!-- /commandBox -->

<h4>解説</h4>
<div class="section">
<p class="txt">「受注」エンティティから「顧客」へのリレーション「出荷先顧客」を追加しました。</p>
<!--/section--></div>




<h4 class="caption" id="h4_8">例題8 受注ヘッダ、受注明細の属性を見直す</h4>
<div class="section">
<p class="txt">まず、業務の現状と要望事項を説明します。それを把握した上で、続く問題に答えなさい。</p>
<p class="txt">業務担当者にヒアリングをすることによって実際に受注を受けるにあたっては、次のような情報も管理していることがわかりました。</p>
<ul>
<li>● 客先希望納期：注文単位の場合もあるし、商品ごとの場合もあります<br>
場合によっては個数を分けて異なる納期で注文という場合も考えられます</li>
<li>● 受注キャンセル：出荷指示がでるまでは、受注のキャンセルを受付ける、ということがわかりました<br>
出荷指示を出した後はキャンセルすることはできず、売上返品という形で処理しています<br>
キャンセルの単位は、受注すべての場合もあるし、受注明細の商品単位の場合もあります</li>
</ul>
<!--/section--></div>


<div class="section">
<h5 class="quiz-title">Ｑ&nbsp;問題</h5>
<p class="txt">上記の要件を満たすために必要な変更をER図に加えてください。</p>
<!--/section--></div>

<div class="section">
<h5 class="answer-title">Ｈ&nbsp;ヒント</h5>
<p class="txt">「客先希望納期」を「受注明細」エンティティで管理すれば、同じ商品でも希望納期の違いによって別の明細行を作成することができます。<br>
すべての受注明細の希望納期が同じであるという前提であれば、「受注」エンティティで「客先希望納期」を管理すればよいといえます。</p>
<p class="txt">キャンセルは、「受注」単位でも、「受注明細」単位でも対応できる必要があります。<br>
また、出荷指示がでるまで、という制限があるので、ステータスで出荷指示を管理し、アプリケーションで判断できるようにする必要があります。</p>
<!--/section--></div>

<div class="section">
<h5 class="answer-title">Ａ&nbsp;解答</h5>
<p class="txt">ER図に変更はありません。</p>
<!--/section--></div>


<div class="commandBox">
<div class="command">
<table width="100%">
<tr><td colspan="2"><strong>受注</strong></td><td colspan="2">：属性追加と属性名変更</td></tr>
<tr><td style="width:20px;">*</td><td style="width:150px;">受注注文番号</td><td style="width:80px;">&nbsp;</td><td style="width:200px;">&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>客先注文番号</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注日付</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注顧客コード</td><td>（FK1）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>出荷先顧客コード</td><td>（FK2）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注社員コード</td><td>（FK3）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>値引き承認社員コード</td><td>（FK4）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注部門コード</td><td>（FK5）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き承認フラグ</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き非承認理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>値引き詳細番号</td><td>（FK6）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>消費税額</td><td>（導出）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>税抜受注金額合計</td><td>（導出）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>キャンセルフラグ</td><td>&nbsp;</td><td>1.</td></tr>
<tr><td>&nbsp;</td><td>摘要</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td colspan="4" >&nbsp;</td></tr>
<tr><td colspan="2">スーパータイプ：<strong>受注明細</strong></td>
<td colspan="2">：属性追加</td></tr>
<tr><td>*</td><td>受注注文番号</td><td>（FK1）</td><td>&nbsp;</td></tr>
<tr><td>*</td><td>商品コード</td><td>（FK2、FK3）</td><td>&nbsp;</td></tr>
<tr><td>*</td><td>客先希望納期日付</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>価格種別コード</td><td>（FK3）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>商品価格適用開始日</td><td>（FK3）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き承認フラグ</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>営業値引き非承認理由</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>値引き詳細番号</td><td>（FK4）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>消費税額</td><td>（導出）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>税抜金額</td><td>（導出）</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>予定納期日付</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>受注数量</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>変更後最終受注数量</td><td>&nbsp;</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>キャンセルフラグ</td><td>&nbsp;</td><td>1.</td></tr>
<tr><td>&nbsp;</td><td>ステータス</td><td>&nbsp;</td><td>2.</td></tr>
</table>
</div>
</div><!-- /commandBox -->


<h4>解説<br>（注：番号は解答中の番号と対応します。番号が記載されていない解説は全体に当てはまります）</h4>
<div class="section">
<ul>
<li>● 「受注明細」エンティティに「客先希望納期日付」属性を追加します<br>
同じ商品でも、異なる希望納期であれば、別オカレンスとして管理する必要があるため、「客先希望納期日付」もー意識別子の一部になります</li>
<li>1. 「キャンセルフラグ」は、「受注」と「受注明細」の両方に属性として追加します<br>
値はデフォルト値で0を設定し、キャンセル時に1を設定します</li>
<li>2. ステータス属性では、これまで、</li>
<li style="padding-left:2em;">● 仮受注</li>
<li style="padding-left:2em;">● 受注確定</li>
<li style="padding-left:2em;">● 納期確定</li>
<li>を管理していましたが、これに、「出荷指示清」を追加します<br>
ステータスの使用方法として、「受注確定」後、営業判断による値引きがなければ即時に「出荷指示」をだすことができます<br>
営業判断による値引きがあった場合、「営業値引き承認フラグ」に承認の値を確認できた場合、「出荷指示」処理が行われます。</li>
</ul>
<div class="grayBox">
<p><img src="./images/613-01.gif" width="500" height="575" alt="図6-8 6.1節全体のER図"></p>
<p class="boxTxt">図6-8 6.1節全体のER図</p>
<!--/.grayBox--></div>
<!--/section--></div>



</body></html>