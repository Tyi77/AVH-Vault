- Fog 不變動，但每個人的 visibility 應該要是不一樣的。因為 eye height 不同，導致每個人的 extinction coefficient 會不同，因此 visibility 就會不同。
- 直接使用那篇論文的visibility就可以了
# 第二版Visibility
## Contrast 的定義
- ![[Pasted image 20251121230654.png]] (11.1)
- B 也就是 Luminance，單位是 $cd/m^2$ ，
## visual range 式子的由來
- 把 33.1 式子拿來用
	- ![[Pasted image 20251121224230.png]]
	- 這兩個式子是同個式子，只是參數的位置擺放的不一樣
- 上面的式子是從 14.2 推算而來的
	- ![[Pasted image 20251121224416.png]]
	- 而因為是 Horizontal Vision，所以變成 16.2 的式子
		- ![[Pasted image 20251121225400.png]]
		- background luminance 不管多遠都會是一樣的，所以 $B_0' = B_R'$ ，也就是那一項會是 1 ，自然就消失不見了。
- $\varepsilon$ 的定義是物體快看不見的時候的臨界contrast，跟visual range的定義一致，所以 33.1 的式子才長那樣。在 16.2 的式子中把 R 帶上 V、把 $C_R$ 帶上 $\varepsilon$
## 把公式放到Unity中
- 無法真正模擬B。因為遊戲引擎本身不會做到這件事情，而且還需要透過相機做人工校正，過於複雜。
- 但如果只是要用到 C 而已的話，那只要讓 $k = B_{Unity} / B_{real}$ (固定比例) 成立，Unity 中的 C 就會跟實際的 C 一樣了。這樣後面要用到 C 的公式就不會出問題了。 