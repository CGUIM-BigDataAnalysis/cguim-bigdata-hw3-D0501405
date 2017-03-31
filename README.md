長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest) ##
```

    ## Warning: package 'rvest' was built under R version 3.2.5

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.2.5

``` r
totalpage<- NULL
for(i in 4635:1){
    N<-paste0("https://www.ptt.cc/bbs/NBA/index",as.character(i),".html")
    NContent<-read_html(N)
    post_title <-NContent %>% html_nodes(".title") %>% html_text()
    post_PushNum<- NContent %>% html_nodes(".nrec") %>% html_text()
    post_Author<- NContent %>% html_nodes(".author") %>% html_text()
    temp<-data.frame(title=post_title, pushnum=post_PushNum, author=post_Author)
    totalpage<- rbind(totalpage,temp)
if(nrow(totalpage)>100){
    break
}
    }
```

爬蟲結果呈現
------------

``` r
#
knitr::kable(totalpage) ##
```

| title                                               | pushnum | author       |
|:----------------------------------------------------|:--------|:-------------|
| Re: \[討論\] 勇士防守怎麼那麼猛??                   | 9       | CYPer        |
| \[新聞\] 球迷怨輪休 杜蘭特：沒錢看球的更可憐        | X3      | zzyyxx77     |
| \[新聞\] 勇士迷快看　杜蘭特歸隊時間有譜了           | 30      | JAL96        |
| \[Live\] 籃網 @ 活塞                                | 爆      | Rambo        |
| \[討論\] nba季後賽程表                              | 16      | leyi12       |
| \[Live\] 騎士 @ 公牛                                | 爆      | Rambo        |
| \[Live\] 湖人 @ 灰狼                                | 36      | Rambo        |
| Re: \[討論\] nba季後賽程表                          | 10      | Aretimis7345 |
| \[Live\] 快艇 @ 太陽                                | 6       | Rambo        |
| \[討論\] 林書豪是甲還是甲上呢                       | X3      | goal56       |
| \[BOX \] Nets 89:90 Pistons 數據                    | 57      | Rambo        |
| \[花邊\] James模仿Lonzo Ball的投籃姿勢              | 7       | ericl1234567 |
| \[Live\] 火箭 @ 拓荒者                              | 爆      | Rambo        |
| \[情報\] LBJ例行賽生涯得分升至歷史第七(超越Shaq)    | 53      | MrSatan      |
| \[BOX \] Lakers 104:119 Timberwolves 數據           | 爆      | Rambo        |
| \[BOX \] Cavaliers 93:99 Bulls 數據                 | 99      | Rambo        |
| \[情報\] 騎士教練Lue：今晚是一個重回正軌的好機會    | 74      | PaulDavis    |
| \[討論\] 勒布朗到底強在哪裡？                       | 67      | phantomboy   |
| \[討論\] 有人跟我一樣比較喜歡以前的LBJ嗎 ?          | 99      | a125567365   |
| \[閒聊\] 公牛TNT直播時主場20連勝                    | 12      | dragon803    |
| Re: \[討論\] NBA Store廣告意涵                      | 4       | iammatrix    |
| Re: \[討論\] 該怎麼阻止勇士一波流的打法?            | 5       | stocktonty   |
| \[新聞\] NBA》傳奇中鋒排名 歐尼爾認為自己只排       | 爆      | lovea        |
| \[花邊\] 勇馬大戰票價創聖安東尼奧近十年第四高       | 11      | Yui5         |
| \[新聞\] NBA》自己的紀錄自己刷 柯瑞單季289三分      | 57      | thanksyou    |
| 如果籃球改成這樣                                    | X1      | riddickwu    |
| \[情報\] ★今日排名(2017.03.30)★                     | 4       | Rambo        |
| \[新聞\] 衛少57分大三元 魔術主場倒戈高喊MVP！       | 7       | iam168888888 |
| Re: \[討論\] NBA Store廣告意涵                      | 1       | google60411  |
| \[討論\] 這波勇士九連勝的一些數據                   | 57      | juchii       |
| \[討論\] 為什麼林書豪不交女朋友                     |         | SongLa5566   |
| Re: \[新聞\] NBA》傳奇中鋒排名 歐尼爾認為自己只排   |         | tobyhuang    |
| \[討論\] 若布拉加入騎士是不是就是完全體了?          | 10      | randy225     |
| \[討論\] 今年DPOY                                   | 爆      | sean4712     |
| \[討論\] 17梯前10新秀，高光影片整理                 | 爆      | rabbit529    |
| Re: \[討論\] 近代哪個球員最過譽了                   |         | km10635237   |
| \[討論\] Duncan與Popovich                           | X3      | Feiwer       |
| Re: \[討論\] 若布拉加入騎士是不是就是完全體了?      |         | LeeChi5566   |
| Re: \[討論\] 為什麼林書豪不交女朋友                 | 15      | sasolala     |
| \[討論\] 體能怪物 Zion Williamson                   | 51      | checktime    |
| Re: \[討論\] 該怎麼阻止勇士一波流的打法?            |         | overkill0802 |
| \[心得\] 龜龜精彩的一季 進階數據真漂亮              | 47      | checktime    |
| \[新聞\] 尼克連四年無季後賽　安東尼:真的很難受      | 28      | jhemezuo     |
| \[討論\] 沒有被黑的球星都具備什麼特質               | 爆      | waiting0212  |
| \[新聞\] 主場被灰狼逆轉 喬治怒批隊友態度            | 15      | adam7148     |
| \[花邊\] 馬里安支持衛少MVP 看好西區球隊奪冠         | 40      | adam7148     |
| \[新聞\] 不滿遭撞倒還被吹犯規 小牛球員火大嗆        | 10      | zzzz8931     |
| Re: \[討論\] 該怎麼阻止勇士一波流的打法?            | 23      | djviva       |
| \[討論\] 該怎麼評價Steve Kerr這位教練               | 52      | ericl1234567 |
| \[新聞\] 浪花兄弟合飆52分　勇士本季首勝馬刺         | 16      | JAL96        |
| \[討論\] 今晚我該骰死誰？                           | 4       | Copycat3     |
| \[討論\] 勇士防守怎麼那麼猛??                       | 61      | dxc669       |
| \[討論\] 勇士的大腿真的是KD嗎?                      |         | rrr111222    |
| \[討論\] Kyrie Irving是不是過譽了                   | 98      | KyrieIrving1 |
| \[新聞\] 已能與助教鬥牛 杜蘭特例行賽前可望歸隊      | 14      | iso2288      |
| Re: \[新聞\] 魏少拿大三元打贏爵士 聯盟剩4隊還沒被他 | 9       | checktime    |
| \[討論\] NBA Store廣告意涵                          | 11      | eric7943     |
| \[討論\] KD回歸後 比賽落後時的打法                  | 6       | omare        |
| \[討論\] Mcgee這個球員                              | 62      | yokann       |
| \[新聞\] 騎士近況低迷 厄文：我得承擔責任            | 67      | gt097231     |
| \[討論\] 有人也希望馬刺再一冠嗎?                    | X1      | elgoogle     |
| \[外絮\] 詹姆斯認為卡達珊詛咒了球隊                 | X1      | kyle5241     |
| (本文已被刪除) \[carmeloeat\]                       |         | -            |
| \[討論\] 該怎麼阻止勇士一波流的打法?                | 57      | crowley      |
| \[討論\] K.Leonard的運球                            | 5       | cksxxb123    |
| \[討論\] AD為什麼討論度那麼低 ?                     | 26      | erikaptt     |
| Re: \[討論\] 馬刺可以打到西冠嗎？                   | 5       | rainfruit    |
| \[情報\] VC生涯總得分超越Ray Allen                  | 59      | Wall62       |
| \[BOX \] Jazz 112:82 Kings 數據                     | 6       | Rambo        |
| \[討論\] 東西區季後賽抽籤如何？                     | 12      | mystage      |
| Re: \[情報\] “刺客”Thomas：快艇的奪冠之門已經關     |         | PegasusSeiya |
| Re: \[討論\] 該怎麼阻止勇士一波流的打法?            | 4       | rainfruit    |
| \[討論\] KD和LBJ互換，哪隊比較強                    | 32      | sandiato     |
| \[情報\] Curry本季命中289記三分，史上第二           | 爆      | iefw         |
| \[新聞\] 浪花兄弟合飆52分 勇士逆轉馬刺保龍頭        | 23      | jay0601zzz   |
| \[公告\] NBA 樂透開獎                               | 1       | \[彩券\]     |
| \[情報\] NBA Standings(2017.03.30)                  | 42      | kadasaki     |
| \[BOX \] Wizards 124:133 Clippers 數據              | 46      | hungys       |
| \[情報\] David West談被馬刺球迷噓：這就是NBA        | 99      | Turtle100    |
| \[討論\] 第一輪若雷霆V.S.火箭 會影響MVP選情嗎?      | 63      | FAYeeeeeeee  |
| \[BOX \] Thunder 114:106 Magic 數據                 | 爆      | Rambo        |
| \[情報\] 龜龜大三元場次一覽表                       | 49      | checktime    |
| \[討論\] 勇刺之戰之勝負我見                         | X4      | CurryMvp     |
| \[BOX \] Hornets 110:106 Raptors 數據               | 14      | Rambo        |
| \[BOX \] Heat 105:88 Knicks 數據                    | 33      | Rambo        |
| \[BOX \] Bucks 103:100 Celtics 數據                 | 46      | Rambo        |
| \[Live\] 巫師 @ 快艇                                | 15      | Rambo        |
| \[Live\] 爵士 @ 國王                                | 2       | Rambo        |
| \[情報\] Westbrook 創下史上最高得分大三元           | 爆      | thnlkj0665   |
| \[新聞\] I.湯瑪斯飆32分沒用 塞爾提克又把東部第      | 35      | pneumo       |
| \[討論\] 過場音樂                                   | 4       | a167182100   |
| \[BOX \] Pacers 97:110 Grizzlies 數據               | 48      | hungys       |
| R：\[專欄\] 塞爾蒂克再升級 東區天平正在改變LYS      | X2      | andy80419    |
| \[BOX \] Mavericks 118:121 Pelicans 數據            | 54      | hungys       |
| \[討論\]溜馬 pg. vs 尼克melo                        | 33      | kiske011     |
| \[討論\] 1961-62 該季MVP投票情況                    | 29      | checktime    |
| \[討論\] 有發生過主將受傷卻意外排毒成功嗎？         | 62      | Silmeria     |
| \[BOX \] Warriors 110:98 Spurs 數據                 | 爆      | Rambo        |
| \[討論\] KD對於勇士重要性                           | 80      | kentisking   |
| \[討論\] 馬刺可以打到西冠嗎？                       | 56      | lopopo001    |
| \[討論\] 有一種拋投叫？（東尼拋克獲勝！）           | 爆      | gn00167236   |
| \[情報\] Rookie Ladder Week 21                      | 17      | Vedan1213    |
| \[情報\] 溜馬嘗試簽回Lance Stephenson               | 17      | dragon803    |
| \[情報\] 溜馬與Stephenson簽下三年1200萬合約         | 51      | k960674      |
| \[情報\] 前籃網新秀有興趣歸化菲律賓                 | 30      | pipi8963     |
| \[Live\] 老鷹 @ 七六人                              | 4       | Rambo        |
| \[Live\] 雷霆 @ 魔術                                | 爆      | Rambo        |
| \[Live\] 公鹿 @ 超賽                                | 14      | Rambo        |
| \[Live\] 黃蜂 @ 暴龍                                | 4       | Rambo        |
| \[Live\] 熱火 @ 尼克                                | 5       | Rambo        |
| \[Live\] 溜馬 @ 灰熊                                | 7       | Rambo        |
| \[Live\] 小牛 @ 鵜鶘                                | 14      | Rambo        |
| \[討論\] Curry+CP3                                  |         | harry1234585 |
| \[專欄\] 塞爾蒂克再升級 東區天平正在改變LYS         | X8      | zzyyxx77     |
| Re: \[專欄\] 塞爾蒂克再升級 東區天平正在改變LYS     | 70      | st900278     |
| \[Live\] 勇士 @ 馬刺                                | 爆      | Rambo        |
| (本文已被刪除) \[feyako\]                           | 16      | -            |
| \[情報\] KD復原情況良好                             | 25      | sthho        |
| \[討論\] 07馬刺打騎士，是實力差距最大的總冠嗎       | 爆      | s106667      |
| \[BOX \] Hawks 99:92 Sixers 數據                    | 19      | Rambo        |

解釋爬蟲結果
------------

``` r
#
nrow(totalpage)
```

    ## [1] 120

共找出120篇

``` r
#
table(totalpage$author)
```

    ## 
    ##   a125567365 Aretimis7345        CYPer    dragon803 ericl1234567 
    ##            1            1            1            2            2 
    ##       goal56        JAL96       leyi12      MrSatan    PaulDavis 
    ##            1            2            1            1            1 
    ##   phantomboy        Rambo     zzyyxx77    checktime       Feiwer 
    ##            1           26            2            5            1 
    ##  google60411 iam168888888    iammatrix       juchii   km10635237 
    ##            1            1            1            1            1 
    ##   LeeChi5566        lovea    rabbit529     randy225    riddickwu 
    ##            1            1            1            1            1 
    ##     sasolala     sean4712   SongLa5566   stocktonty    thanksyou 
    ##            1            1            1            1            1 
    ##    tobyhuang         Yui5     adam7148     Copycat3       djviva 
    ##            1            1            2            1            1 
    ##       dxc669     eric7943     gt097231      iso2288     jhemezuo 
    ##            1            1            1            1            1 
    ## KyrieIrving1        omare overkill0802    rrr111222  waiting0212 
    ##            1            1            1            1            1 
    ##       yokann     zzzz8931            -       [彩券]    cksxxb123 
    ##            1            1            2            1            1 
    ##      crowley     elgoogle     erikaptt  FAYeeeeeeee       hungys 
    ##            1            1            1            1            3 
    ##         iefw   jay0601zzz     kadasaki     kyle5241      mystage 
    ##            1            1            1            1            1 
    ## PegasusSeiya    rainfruit     sandiato    Turtle100       Wall62 
    ##            1            2            1            1            1 
    ##   a167182100    andy80419     CurryMvp   kentisking     kiske011 
    ##            1            1            1            1            1 
    ##    lopopo001       pneumo     Silmeria   thnlkj0665   gn00167236 
    ##            1            1            1            1            1 
    ## harry1234585      k960674     pipi8963      s106667     st900278 
    ##            1            1            1            1            1 
    ##        sthho    Vedan1213 
    ##            1            1

Rambo 發表了最多篇的文章

Live的推文比其他討論多
