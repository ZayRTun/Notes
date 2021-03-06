**Home**
- [Home](../index.md)
---

# Alpine Js Crash Course

## General Workflow of Alpine

```html
<body>
    <div x-data="game()" class="px-10 flex items-center justify-center min-h-screen">
        <h1 class="fixed top-0 right-0 p-10">
            <span x-text="points" class="font-bold text-5xl"></span>
            <span class="font-bold">pts</span>
        </h1>


        <div class="flex-1 grid grid-cols-4 gap-10">
            <template x-for="card in cards">
                <div>
                    <button x-show="! card.cleared" :style="'background: ' + (card.flipped ? card.color : '#999')" class="w-full h-32" @click="flipCard(card)">
                    </button>
                </div>
            </template>
        </div>
    </div>

    <script>
        function game() {
            return { 
                cards: [
                    {color: 'green', flipped: false, cleared: false},
                    {color: 'red', flipped: false, cleared: false},
                    {color: 'blue', flipped: false, cleared: false},
                    {color: 'yellow', flipped: false, cleared: false},
                    {color: 'green', flipped: false, cleared: false},
                    {color: 'red', flipped: false, cleared: false},
                    {color: 'blue', flipped: false, cleared: false},
                    {color: 'yellow', flipped: false, cleared: false},
                ],
                
                get flippedCard() {
                    return this.cards.filter(card => card.flipped);
                },
                
                get clearedCards() {
                    return this.cards.filter(card => card.cleared);
                },
                
                get remainingCards() {
                    return this.cards.filter(card => ! card.cleared)
                },
                
                get points() {
                    return this.clearedCards.length;
                },
                
                flipCard(card) {
                    card.flipped = !card.flipped
                    
                    if(this.flippedCard.length === 2) {
                        if (this.hasMatch()) {
                            setTimeout(() => {
                                this.flippedCard.forEach(card => card.cleared = true);
                            }, 500);
                            
                            if (! this.remainingCards.length) {
                                alert('You have won!');
                            }
                        }
                        
                        setTimeout(() => {
                            this.flippedCard.forEach(card => card.flipped = false);
                        }, 500);
                    }
                },
                
                hasMatch() {
                    return this.flippedCard[0]['color'] === this.flippedCard[1]['color'];
                }
            }
        }
    </script>
</body>

```
