隣と同じ色かという配列を考える．c[i]=0ならビーズiとi+1は同じ,c[i]=1ならビーズiとi+1は異なるとする．  
ビーズ0の色と配列cを決めるとビーズの配置が1つに決まる．  
よって条件を満たす配列cを求める問題だと思って解く．  
ビーズl～rの種類数が1という条件はc[l]=c[l+1]=...=c[r-1]=0と言い換えられる．  
ビーズl～rの種類数が2という条件はc[l],c[l+1],...,c[r-1]の中で1つ以上が1であると言い換えられる．  
よって種類数が1の区間を全部0にして残りの決まっていない場所を1にすればいい．  

種類数1の区間の処理について，  
左から順に見ていってその地点を覆う種類数1の区間の数を数える．  
その地点を覆う区間が1個以上あるなら配列cを0にすればいい．  
左から順に見ていくのである区間l～rがある場合lに来たタイミングで数を+1してrに来たタイミングで-1すればよい  
よって新しい配列dを用意して，各区間l～rについてd[l]に+1,d[r]に-1をする．  
その後配列dの累積和をとると各場所を覆う区間の個数が分かる．  

上の処理で0にならなかった場所をすべて1にする．  
その後種類数2の条件を満たすかを調べる．これは配列cでのある区間の1の個数が分かればいいので累積和を使えばよい．  
条件を満たすなら最初の文字を'R'にしてそれ以降の文字は配列cを元に構成できる．
