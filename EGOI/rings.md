ある頂点についてその頂点と直接つながっている頂点の数をその頂点の次数とする．
重大な頂点の条件は，その頂点をグラフから除いたときに残ったグラフが  
1.すべて次数2以下である  
2.ループがない  
の二つを満たすと言い換えられる．

辺を追加したときの頂点の次数は簡単に更新できる．
次の場合分けをする．
- すべての頂点が次数2以下のとき  
    各連結成分は鎖状または単純な輪っか状になっている．
    - ループがない場合(鎖のみの場合)  
    すべての頂点が重大である．
    - ループがある場合  
    取り除いたときにループが残ってはいけないので，重大な頂点はループ内である．
        - 輪っか状の連結成分が1つのみの場合  
        その連結成分すべてが重大な頂点である．
        - 輪っか状の連結成分が2つ以上ある場合  
        重大な頂点はない
    
    これらの判定は頂点の次数と，Union Findによるループの有無と各連結成分の頂点数を辺を追加するたびに更新するとできる．
- 次数3の頂点があるとき  
    重大な頂点の候補はその頂点と，その頂点と直接つながっている頂点の高々4つのみである．  
    つまり一度次数3の頂点が現れるとそれ以降は重大な頂点の候補として4頂点しか考えなくてよい．  
    したがってその4頂点それぞれについて実際にその頂点を取り除いたときに条件を満たすかを調べてやる（次数2以下かつループがない）．

    候補が4つになった時点で，その4頂点それぞれについて，その頂点を除いた4パターンのグラフを作って，頂点の次数とUnion Find によるループの有無を調べる．これ以降辺が追加されるときも4つのグラフそれぞれに辺を追加して条件を満たすかを調べていけばよい．