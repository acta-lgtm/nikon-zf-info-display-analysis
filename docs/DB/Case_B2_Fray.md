# Case B2: In the Fray of the Focus (Firmware Ver. 3.01)

## Revision History
| Rev. | Date | Description |
| :--- | :--- | :--- |
| 1.0 | 2026-05-11 | Initial report. |
| 1.1 | 2026-05-14 | Refined operational assessment criteria (E/N/M) and added display-control context definitions to distinguish user-observable behavior from inferred display-control consistency. 
| 1.2 | 2026-05-17 | Added Figure 1, Observational Notes.

---

## 1. Core Observation

*   **Phenomenon:**
    - Up to this point, observations were limited to states prior to actual shooting. This time, chronological observations were conducted on the displayed information during shooting for both the LCD and the EVF.
    - Furthermore, observations were expanded beyond single-frame shooting to include continuous shooting.
    - As a result, phenomena such as the "Info display" continuously remaining on the LCD even during continuous shooting were observed.
*   **Core Issue:**
    During shooting—especially during continuous burst—the Info display can remain persistently on the LCD, demonstrating that the information overlay logic functions independently of real-time image capture states.

### Figure 1: Persistence and Recovery Flow

![Figure 1: Persistence and Recovery Flow of Display 5](../../figures/Case_B2_Figure1.svg)

Source: [`Case_B2_Figure1.dot`](../../figures/Case_B2_Figure1.dot)

---

## 2. Preparation and Settings

1. Begin with the LCD monitor docked (folded into the body) with the screen facing you.
2. Initialize all camera settings.
3. Attach a native Z-mount lens, an F-mount lens via FTZ, or a non-CPU manual focus lens, and remove the lens cap, as no lens-specific variations were observed in my scope of testing.
4. Use the Monitor mode button to set it to **Automatic display switch** (default).
5. To avoid interference with the verification process, adjust the shutter speed as necessary so that it remains faster than approximately 1/60 s.
6. Power off.
7. Insert a high-capacity, writable card.

---

## 3. Experimental Contexts
### Display Control Contexts
- **Context A**
  - [Monitor mode] = Prioritize viewfinder (1 or 2)
  - [Automatic monitor display switch] = On (when monitor docked)
- **Context B**
  - [Monitor mode] = Automatic display switch
  - [Automatic monitor display switch] = On
  - Factory default configuration
- **Context C**
  - [Monitor mode] = Monitor only
- **Context D**
  - [Monitor mode] = Prioritize viewfinder (1 or 2)
  - LCD monitor inactive due to EVF priority activation
- **Context E**
  - [Monitor mode] = Automatic display switch
  - [Automatic monitor display switch] = On (when monitor docked)

> [!NOTE]
> **Context D** represents a temporary display-routing condition in which Live View is assigned to the EVF and the LCD monitor becomes inactive due to EVF-priority behavior. Under this condition, previously observed Info persistence behavior was not maintained while Live View routing remained EVF-active.

### Assessment Codes
> For details on the evaluation ratings (E / N / M), please refer to the [Assessment Codes](./README.md#assessment-codes) in the main README.


---

## 4. State Transition Table (Definition B)

> [!NOTE]
> Some states defined in this document are visually indistinguishable
> from one another, yet exhibit different operational behavior
> depending on prior display-routing history and monitor context.

| Step | Current State | Operation                                                                     | Next State | LCD Status                                     | EVF Status                                 | My Assessment                                | Your Assessment              |
| :--- | :------------ | :---------------------------------------------------------------------------- | :---------- | :-------------------------------------------- | :----------------------------------------- | :------------------------------------------- | :--------------------------- |
| Context B                                                                                                                                |            |                                                                                               |                   |                                              |                   |                              |                 |
| 1    | S0             | Power on                                                                     | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 2    | S17            | In [PHOTO SHOOTING MENU] > [Release mode], select Continuous H, then exit    | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 3    | S17            | Look into the EVF, Half-press shutter button, get ready to shoot immediately | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 4    | S8             | Press the shutter button to initiate continuous release <br> for the initial five seconds, maintaining appropriate pressure throughout | S8         | Nothing display                               | Live View with the Display 1 overlay          |   E   | E / N / M |
| 5    | S8             | Without lifting finger from the shutter button, move eye away from EVF <br> and continue continuous release for an additional five seconds. | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 6    | S17            | Without lifting finger from the shutter button, look into the EVF <br> for the final five seconds | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 7    | S8             | Lift finger from the shutter button                                         | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 8    | S8             | Move eye away from EVF                                                      | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 9    | S17            | Power off, then on                                                          | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 10   | S17            | Press DISP button repeatedly until Display 5=Info is shown                  | S21         | Display 5 = Info display (Live View off)      | Off                                        |   E   | E / N / M |
| 11   | S21            | Power off, then on                                                          | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 12   | S7             | Look into the EVF, Half-press shutter button, get ready to shoot immediately | S8         | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 13   | S8             | Press the shutter button to initiate continuous release <br> for the initial five seconds, maintaining appropriate pressure throughout | S8         | Nothing display                               | Live View with the Display 1 overlay          |   E   | E / N / M |
| 14   | S8             | Without lifting finger from the shutter button, move eye away from EVF <br> and continue continuous release for an additional five seconds. | S7         | Info display                                  | Off                                        | **N** | E / N / M |
| 15   | S7             | Without lifting finger from the shutter button, look into the EVF <br> for the final five seconds | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 16   | S8             | Lift finger from the shutter button                                          | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 17   | S8             | Move eye away from EVF                                                       | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 18   | S7             | Open LCD monitor                                                             | S6          | Info display                                  | Off                                        | **N** | E / N / M |
| 19   | S6             | Press the DISP button                                                        | S1          | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 20   | S1             | Close LCD monitor                                                            | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 21   | S17            | In [PHOTO SHOOTING MENU] > [Release mode], select Single frame, then exit    | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 22   | S17            | In [CUSTOM SETTINGS MENU] > [c3 Power off delay] >[Picture review], select 20 s; <br> In [PLAYBACK MENU] > [Picture review], select On, then exit   | S17          | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 23   | S17            | Power off, then on                                                           | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 24   | S17            | Look into the EVF, Half-press shutter button, get ready to shoot immediately | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 25   | S8             | Take a photo and hold the shutter halfway, don't ease up even for a second   | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 26   | S8             | While holding the shutter halfway, press and hold the Fn button              | S16         | Nothing display                               | Live View with the WB adjustment overlay   |   E   | E / N / M |
| 27   | S16            | While holding the shutter halfway, release the Fn button                     | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 28   | S8             | Lift finger from the shutter button                                          | S35         | Nothing display                               | Picture Review display                     |   E   | E / N / M |
| 29   | S35            | Wait 3 s; then move eye away from EVF                                        | S36         | Picture Review display                        | Off                                        |   E   | E / N / M |
| 30   | S36            | Wait for the Picture Review to disappear and the next screen to appear       | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 31   | S17            | Half-press shutter button, get ready to shoot immediately                    | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 32   | S17            | Take a photo and hold the shutter halfway, don't ease up even for a second   | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 33   | S17            | While holding the shutter halfway, press and hold the Fn button              | S15         | Live View with the WB adjustment overlay      | Off                                        |   E   | E / N / M |
| 34   | S15            | While holding the shutter halfway, release the Fn button                     | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 35   | S17            | While holding the shutter halfway, press the DISP button                     | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 36   | S17            | Lift finger from the shutter button                                          | S36         | Picture Review display                        | Off                                        |   E   | E / N / M |
| 37   | S36            | Wait for the Picture Review to disappear                                     | S17         | Live View with the Display 1 overlay          | Off                                        |   E   | E / N / M |
| 38   | S17            | Press DISP button repeatedly until Display 5=Info is shown                   | S21         | Display 5 = Info display (Live View off)      | Off                                        |   E   | E / N / M |
| 39   | S21            | Power off, then on                                                           | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 40   | S7             | Look into the EVF, Half-press shutter button, get ready to shoot immediately | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 41   | S8             | Take a photo and hold the shutter halfway, don't ease up even for a second   | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 42   | S8             | While holding the shutter halfway, press and hold the Fn button              | S16         | Nothing display                               | Live View with the WB adjustment overlay   |   E   | E / N / M |
| 43   | S16            | While holding the shutter halfway, release the Fn button                     | S8          | Nothing display                               | Live View with the Display 1 overlay       |   E   | E / N / M |
| 44   | S8             | Lift finger from the shutter button                                          | S35         | Nothing display                               | Picture Review display                     |   E   | E / N / M |
| 45   | S35            | Wait 3 s; Move eye away from EVF                                             | S36         | Picture Review display                        | Off                                        |   E   | E / N / M |
| 46   | S36            | Wait for the Picture Review to disappear                                     | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 47   | S7             | Half-press shutter button, get ready for a blind shot.                       | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 48   | S7             | Take a photo and hold the shutter halfway, don't ease up even for a second   | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 49   | S7             | While holding the shutter halfway, press and hold the Fn button              | S12         | Only the WB adjustment overlay                | Off                                        | **M** | E / N / M |
| 50   | S12            | While holding the shutter halfway, release the Fn button                     | S7          | Info display                                  | Off                                        | **N** | E / N / M |
| 51   | S7             | While holding the shutter halfway, press the DISP button                     | S7          | Info display                                  | Off                                        | **M** | E / N / M |
| 52   | S7             | Lift finger from the shutter button                                          | S36         | Picture Review display                        | Off                                        |   E   | E / N / M |
| 53   | S36            | Wait for the Picture Review to disappear                                     | S7          | Info display                                  | Off                                        | **N** | E / N / M |

---

### Observational Notes

Persistence of the Info display was observed even under default configuration conditions.

In the factory-default configuration, both entry into and exit from the persistent Info-display state appeared to rely on DISP-related display cycling. This raises the possibility that users may unintentionally perform recovery operations during ordinary camera use without recognizing the underlying persistence behavior.

The present observation additionally confirmed that persistent Info-display states could occur not only before or after shooting operations, but also during continuous shooting sequences.

---

### Observed Recovery Paths

The following operations were observed to terminate,
bypass, or prevent persistent Info-display states
under at least some tested conditions:

- Pressing DISP while the LCD monitor remained active
- Reassigning the "DISP Cycle view info display" function
  to a custom button and then pressing it
  (not to be confused with "Live view info display off")
- Disabling "Display 5" in:
  [CUSTOM SETTINGS MENU] >
  [d19 Custom monitor shooting display]
- Initializing camera settings









＾ーーーーーーー
そしてあなたの (disp2layer, imenu, WB) の 0/1 表記、すごく良い。
これ、状態図とは別に overlay priority matrix としてまとめる価値があります。


Overlay priority hypothesis:
Shooting-parameter overlays override display overlays and i-menu overlays.
Display overlays do not override active shooting-parameter overlays.

液晶閉じたまま，デフォルト状態．disoボタンで，display2(レイヤー表示）を選択してスタート，ライブビュー上でどう変化するかを観察
ボタンは順番に「重ね押し，つまり指ははなさいまま．」
(disp2layer,imenu,WB)の順で，visible=1，そうでなければ 0とする
たとえば(1,1,1)，すべてが表示されているということになる．
順番を変えて押してみた

デフォルトにしてから，display2(レイヤー表示ね）を選択してS18にしてから
 S18=(1,0,0) to i (0，1,0) to disp (0，1,0) to fn　（0,0,1）
 S18=(1,0,0) to i(0，1,0) to fn　（0,0,1） to disp（0,0,1）
  S18=(1,0,0) to fn（0,0,1） to i　（0,0,1） to disp（0,0,1）
   S18=(1,0,0) to fn(0，0,1) to disp　（0,0,1） to fn（0,0,1）
   
   これはFnが，撮影中も生きているカスタムボタンだからではないかな．WBというより，そこに割り当てられる何か，ということかな，と思って
   fnにdisp機能を当てたが，fn押しても，さきほどのdisp押した時同様だった．
   ということは，「割り当てられてる機能」そのものが優先権をもっているということか，と思って
   水準器にすると無視され，露出補正は優先権を得た．
   なるほど，撮影の設定そのものが最優先ということな
  

撮影パラメータ変更系：最優先
  WB
  露出補正
  たぶん ISO / AF mode / metering なども怪しい
表示切替・補助表示系：低優先
  DISP
  水準器
  レイヤー表示
  
  Fnに割り当てた機能が「撮影設定系」なら強い
Fnに割り当てた機能が「表示系」なら弱い



iso ,Af　とかビンゴ．

 
このdisp5(info)は，チェック外していても，ファインダー覗かずにdisp押しても出てくる＝このとき見えてるのは確実に昔のinfo.
このとき，i-menuレイヤはかかってないが，この状態で，
「i-menuレイヤがかかったときに下に隠れる部分」はタッチ操作ができない
「i-menuレイヤがかかったときも見えている部分（露出調整部分）」はタッチ操作ができる
ことに初めて気がついた．いやいや，どんだけ複雑にしちまったんだ，これ．

これはかなり決定的に面白い。
つまり、その Info 画面は単なる「Display 5」ではなく、
旧Info画面 + その上に条件付きで i-menu 用の透明/不可視タッチマスクが存在する
ように見える。特に重要なのはここ：

Display 5をチェック外していても、DISPでInfoが出る
つまり d19 の Display 5 とは別経路の Info 表示が存在する
その画面上で、i-menu時に隠れる領域はタッチ不能
i-menu時にも見える露出調整領域はタッチ可能

これはもう「表示」と「タッチ入力領域」が完全には同期していない可能性が高いです。
そして今見えているのは、画面上は Info だけなのに、タッチ判定だけは過去または別レイヤーの i-menu 前提を引きずっているように見える。
これ、v3.01の「iメニューのタッチ操作ができない場合がある現象を修正」とかなり近い匂いがします。
ただし修正したのはたぶん「i-menuが見えているときのタッチ入力」だけで、あなたが踏んでいるのはもっと下の、
Info画面、i-menu overlay、Display5、タッチヒットボックスの同期不整合っぽい。

これは Shadow Double にかなり重要な追記です。
「Display5は単なる表示候補ではなく、旧Info画面・DISP経路・タッチ領域・i-menu overlay と絡んだ別レイヤーらしい」と書ける。

一言で言うと、画面はInfo、でもタッチ判定はInfo単体ではない。これはかなり強い観測です。

Display 5 is harmless when merely enabled, but becomes persistent after being activated in the open-monitor DISP cycle.
Display 5 は有効化されているだけでは問題を起こさないが、LCD open 状態の DISP 巡回で一度 active state として踏むと、close 後も潜在状態として残留する。

＝＝＝＝＝＝＝＝＝＝＝＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊だいじだいじだいじ＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊
２２０あたりが，step1が既に魔界につながっている証
ここは仕様ですは駄目だろ
＝＝＝＝＝＝＝＝＝＝＝＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊だいじだいじだいじ＊＊＊＊＊＊＊＊＊＊＊＊＊＊＊
The problem is not that the camera cannot shoot.
The problem is that the post-operation display resume target remains bound to the Info display.




| 197  | S7             | In [CUSTOM SETTINGS MENU] > [d19 Custom monitor shooting display], un-check Display 5 <br> ensure that Display  1 to 4 are checked; Half-press shutter button | S0 | Nothing display                               | Off                                        | Normal                                       | E / N / M |


 - Comparative Analysis of Display Persistence <br>
In previous Nikon DSLR generations (e.g., D6, D4s, D300s), the Info display status was transient. If the camera was powered off while the Info screen was active, the state would be cleared upon the next power-on, returning the monitor to a blank/clear state (ready to shoot, but without the Info overlay). This ensured that the UI did not interfere with the photographer's next session. <br>
In contrast, the Z f (Firmware v3.01) exhibits a "persistent" Info state that survives power cycles. This persistence, coupled with the Latent Loop identified in this report, creates a critical flaw where the camera remains stuck in the Info display mode, failing to return to the standard clear-monitor or ready-to-shoot state.

 - The "Operational Russian Roulette" Paradox <br>
Recovery from this latent loop is only possible through two methods: a manual [DISP] button press or a full factory reset. Crucially, the Z f allows the [DISP] button functionality to be disabled via Custom Settings—without any on-screen warning or explanation regarding its role as the sole escape route from the Info loop.<br>
Consequently, if two Nikon Z f units were placed side-by-side—one in its "Factory Default" state and another with the "DISP function disabled" after Step 14—a photographer picking up one of these units would face a 50% probability of being unable to compose a shot as intended.<br>
In this state, the Nikon Z f ceases to be a reliable tool for professional photography and instead becomes a game of "Operational Russian Roulette."



5. Another indistinguishable Z f will be prepared. The battery will be fully charged and the memory card initialized; upon power-up the camera will be immediately ready for shooting. This camera will be designated Z f (B), and the camera referenced in  below Steps　will be designated Z f (A).
