# 21.01.25



## ์ฃผ์ ์ง๋ฌธ



#### ๐ก [Redo ๋ ๋ฌด์์ธ๊ฐ์?](#Redo)

```markdown
Undo๋ "์์ํ๋ก ๋๋๋ฆฌ๋ค"๋ผ๋ ์๋ฏธ์ด๋ค.
๋ฐ๋ผ์ Undo ์์์ ๋ณต๊ตฌ, ๋กค๋ฐฑ์ ์๋ฏธํ๋ค.
ํธ๋์ญ์์ ์ด์  ์ํ๋ก ๋๋๋ฆฌ๋ ๊ฒ์ ์๋ฏธ
์์ ๋กค๋ฐฑ, ์ฝ๊ธฐ ์ผ๊ด์ฑ, ๋ณต๊ตฌ
์ฌ์ฉ์๊ฐ ํ๋ ์์์ ๋ฐ๋๋ก ์งํํจ
```

#### ๐ก [Uedo ๋ ๋ฌด์์ธ๊ฐ์?](#Uedo)

```markdown
์ด์  ์ํ๋ก ๋๋์๊ฐ ํ, ์คํจ๊ฐ ๋ฐ์ํ๊ธฐ ์ ๊น์ง์ ๊ณผ์ ์ ๊ทธ๋๋ก ๋ฐ๋ผ๊ฐ๋ ๊ฒ์ ์๋ฏธํฉ๋๋ค.
redo๋ฅผ ํ๊ธฐ ์ํด์๋ ์ ์์ ์ผ๋ก ์คํ ๋๊ธฐ๊น์ง์ ๊ณผ์ ์ ๊ธฐ๋กํด์ผ ํ๋๋ฐ, ์ด๋ฅผ log๋ผ๊ณ  ํฉ๋๋ค.
๋ณต๊ตฌ์ ์ญํ , ์ค๋ผํด ์๋ฒ์ ๋ฌด์จ ์์ ํ๋ ์ง ๋ชจ๋ redo์ ๊ธฐ๋ก์ด ๋ฉ๋๋ค.(undoํฌํจ)
์ฌ์ฉ์๊ฐ ํ๋ ์์์ ๊ทธ๋๋ก ๋ค์ ํจ
```

<br />

## โญ ๊ฐ๋ ์ ๋ฆฌ

### Redis(Remote Dictionary Server)

```markdown
Redis๋ NOSQL๋ก์ Key-Valueํ์์ ์ ์ฅ์์ด๋ค.
Redis๋ Memcached์ ๋น์ทํ ์บ์ ์์คํ์ผ๋ก์ ๋์ผํ ๊ธฐ๋ฅ์ ์ ๊ณตํ๋ฉด์ ์์์ฑ, ๋ค์ํ ๋ฐ์ดํฐ ๊ตฌ์กฐ์ ๊ฐ์ ๋ถ๊ฐ์ ์ธ ๊ธฐ๋ฅ์ ์ง์ํ๊ณ  ์์ต๋๋ค.
๋ ๋์ค๋ ๋ชจ๋  ๋ฐ์ดํฐ๋ฅผ ๋ฉ๋ชจ๋ฆฌ์ ์ ์ฅํ๊ณ  ์กฐํํฉ๋๋ค. ์ฆ, ์ธ๋ฉ๋ชจ๋ฆฌ ๋ฐ์ดํฐ๋ฒ ์ด์ค์๋๋ค.
์ด ๋ง๋ง ๋ค์ผ๋ฉด Redis๋ ๋ชจ๋  ๋ฐ์ดํฐ๋ฅผ ๋ฉ๋ชจ๋ฆฌ์ ์ ์ฅํ๋ ๋น ๋ฅธ DB๊ฐ ๋ค๋ผ๊ณ  ์๊ฐํ  ์๋ ์์ต๋๋ค.
ํ์ง๋ง ๋น ๋ฅธ ์ฑ๋ฅ์ ๋ ๋์ค์ ํน์ง ์ค ์ผ๋ถ๋ถ ์๋๋ค. ๋ค๋ฅธ ์ธ๋ฉ๋ชจ๋ฆฌ DB๋ค๊ณผ์ ๊ฐ์ฅ ํฐ ์ฐจ์ด์ ์ ๋ค์ํ ์๋ฃ๊ตฌ์กฐ ์๋๋ค.
```



<br />

### Redis ์๋ฃ๊ตฌ์กฐ

<img width="736" alt="์คํฌ๋ฆฐ์ท 2022-01-25 ์ค์  9 22 12" src="https://user-images.githubusercontent.com/60912550/150887249-cdbb3e0a-9b33-424c-a2e4-7af180ad815e.png">

```markdown
์ด๋ ๊ฒ ๋ค์ํ ์๋ฃ๊ตฌ์กฐ๋ฅผ ์ง์ํ๊ฒ ๋๋ฉด ๊ฐ๋ฐ์ ํธ์์ฑ๋ ์ข์์ง๊ณ  ๋์ด๋๊ฐ ๋ฎ์์ง๋ค๋ ์ฅ์ ์ด ์์ต๋๋ค.
์๋ฅผ๋ค์ด, ์ด๋ค ๋ฐ์ดํฐ๋ฅผ ์ ๋ ฌํด์ผํ๋ ์ํฉ์ด ์์ ๋, DBMS๋ฅผ ์ด์ฉํ๋ค๋ฉด DB์ ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๊ณ , ์ ์ฅ๋ ๋ฐ์ดํฐ๋ฅผ ์ ๋ ฌํ์ฌ ๋ค์ ์ฝ์ด์ค๋ ๊ณผ์ ์ ๋์คํฌ์ ์ง์  ์ ๊ทผํด์ผ ํ๊ธฐ ๋๋ฌธ์ ์๊ฐ์ด ๋ ๊ฑธ๋ฆฐ๋ค๋ ๋จ์ ์ด ์์ต๋๋ค.
ํ์ง๋ง In-Memory DB์ธ Redis๋ฅผ ์ด์ฉํ๊ณ  ๋ ๋์ค์์ ์ ๊ณตํ๋ Sorted-Set์ด๋ผ๋ ์๋ฃ๊ตฌ์กฐ๋ฅผ ์ฌ์ฉํ๋ฉด ๋ ๋น ๋ฅด๊ณ  ๊ฐ๋จํ๊ฒ ๋ฐ์ดํฐ๋ฅผ ์ ๋ ฌํ  ์ ์์ต๋๋ค.
```

<br />

### Redis ํน์ง

* ์์์ฑ์ ์ง์ํ๋ ์ธ๋ฉ๋ชจ๋ฆฌ ๋ฐ์ดํฐ ์ ์ฅ์
* ์ฝ๊ธฐ ์ฑ๋ฅ ์ฆ๋๋ฅผ ์ํ ์๋ฒ ์ธก ๋ณต์ ๋ฅผ ์ง์
* ์ฐ๊ธฐ ์ฑ๋ฅ ์ฆ๋๋ฅผ ์ํ ํด๋ผ์ด์ธํธ ์ธก ์ค๋ฉ(Sharding) ์ง์
* ๋ค์ํ ์๋น์ค์์ ์ฌ์ฉ๋๋ฉฐ ๊ฒ์ฆ๋ ๊ธฐ์ 
* ๋ฌธ์์ด, ๋ฆฌ์คํธ, ํด์, ์, ์ ๋ ฌ๋ ์๊ณผ ๊ฐ์ ๋ค์ํ ๋ฐ์ดํฐํ์ ์ง์
* ๋ฉ๋ชจ๋ฆฌ ์ ์ฅ์์์๋ ๋ถ๊ตฌํ๊ณ  ๋ง์ ๋ฐ์ดํฐํ์ ์ง์ํ๋ฏ๋ก ๋ค์ํ ๊ธฐ๋ฅ์ ๊ตฌํ

<br />

### Redis ์ฅ์ 

* ๋ฆฌ์คํธ, ๋ฐฐ์ด ๋ฐ์ดํฐ๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐ ์ ์ฉ
* ๋ฆฌ์คํธ ํ ๋ฐ์ดํฐ ์๋ ฅ, ์ญ์ ๊ฐ MySQL์ ๋นํด 10๋ฐฐ์ ๋ ๋น ๋ฆ
* ์์์ ์ธ ๋ฐ์ดํฐ ๋ณด์กด

<br />

### Redis ์์์ฑ

```markdown
Redis๋ ์ง์์ฑ์ ๋ณด์ฅํ๊ธฐ ์ํด ๋ฐ์ดํฐ๋ฅผ disk์ ์ ์ฅํ  ์ ์์ต๋๋ค.
์๋ฒ๊ฐ ๋ด๋ ค๊ฐ๋๋ผ๋ disk์ ์ ์ฅ๋ ๋ฐ์ดํฐ๋ฅผ ์ฝ์ด์ ๋ฉ๋ชจ๋ฆฌ์ ๋ก๋ฉ์ ํฉ๋๋ค.
๋ฐ์ดํฐ๋ฅผ disk์ ์ ์ฅํ๋ ๋ฐฉ์์ ํฌ๊ฒ ๋ ๊ฐ์ง ๋ฐฉ์์ด ์์ต๋๋ค.
```

* RDB(Snapshotting) ๋ฐฉ์
  * ์๊ฐ์ ์ผ๋ก ๋ฉ๋ชจ๋ฆฌ์ ์๋ ๋ด์ฉ์ disk์ ์ ์ฒด๋ฅผ ์ฎ๊ฒจ ๋ด๋ ๋ฐฉ์
* AOF(Append On File) ๋ฐฉ์
  * Redis์ ๋ชจ๋  Wirte/Update ์ฐ์ฐ ์์ฒด๋ฅผ ๋ชจ๋ logํ์ผ์ ๊ธฐ๋กํ๋ ํํ

### ์์ฝ

* ๋ ๋์ค๋ ๊ณ ์ฑ๋ฅ ํค-๊ฐ ์ ์ฅ์๋ก์ ๋ฌธ์์ด, ๋ฆฌ์คํธ, ํด์, ์, ์ ๋ ฌ๋ ์ ํ์์ ๋ฐ์ดํฐ๋ฅผ ์ง์ํ๋ NoSQL์ด๋ค.