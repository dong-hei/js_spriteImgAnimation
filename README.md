# js_스프라이트 이미지 애니메이션

        2d게임 시절에 성능절약을 위해서 슈퍼마리오,포켓몬,메이플에 사용된 스프라이트 애니메이션,
        요즘은 어디서 스프라이트 애니메이션을 사용하나?
        1.여러가지 환경을 고려한 메모리 자원 절약이 필요한 경우
        2.무거운 앱 위에서 가볍고 화려한 이펙트가 필요한 경우
        3.three.js에서 shader를 쓰지않고 빠르게 애니메이션 효과를 만들때
        
        가로세로 길이 선언(이미지 길이)
        const width = 140
        const height = 140
        const cols = 5
        const rows = 4
        let current = 0
        
        const intervalGap = 1000 / 30 // 1초에 30번실행
      

            const sprite = document.createElement('div')
            sprite.style.position= 'absolute'
            sprite.style.left = e.clientX + 'px'
            sprite.style.top = e.clientY + 'px'
            sprite.style.backgroundImage= 'url("./explosion18.png")'
            sprite.style.width = width + 'px'
            sprite.style.height = height + 'px'
            sprite.style.backgroundSize = `${width * cols}px ${height * rows}px`
            sprite.style.transform = 'translate(-50%, -50%)'
            document.body.append(sprite)

            const intervalId = setInterval(() => {
                const currentCol = current % cols // 나머지
                const currentRow = Math.floor(current / cols) // 몫

                sprite.style.backgroundPosition = `${-width * currentCol}px ${-height * currentRow}px`
                //좌표를 줘서 애니메이션처럼 움직이게 한다. 랜덤함수

                if (++current % (rows * cols) === 0){
                    clearInterval(intervalId)
                    document.body.removeChild(sprite)
                }
            }, 100) // 클릭시 애니메이션이 무한히 반복되는데 current 루프가 끝나면 인터벌을 종료시키고
            // spriteChiled를 지운다
        }
