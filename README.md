# FrontEnd
#### AI writing platform ONEGO Refactoring
<br>
<br>

## Vue.js + Storybook
### Set up Vue Storybook

```
npx -p @storybook/cli sb init
```

### Run
```
npm run storybook
```

### Trouble Shooting
1. Error: error:0308010C:digital envelope routines::unsupported<br>
(Node.js version control)
![스크린샷 2022-04-21 오후 11 38 25](https://user-images.githubusercontent.com/76719920/164483427-47de146c-79ea-4b05-9831-17b3748d27ed.png)

- 버전 확인
```
node -v
```

<br>

- Cache 삭제
```
sudo npm cache clean --force
```

<br>

- n 플러그인 설치 (If install n you can manage easier Node.js version.)
```
sudo npm install -g n
```

<br>

- 안정적 버전 설치 (If error message about permission denied, add at the front sudo.)
```
n lts
```

<br>

- 다운로드 목록 보기 (Select version with enter key and install that version.)
```
n
```



