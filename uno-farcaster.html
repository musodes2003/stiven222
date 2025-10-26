import React, { useState, useEffect } from 'react';
import { RotateCw } from 'lucide-react';

const UnoGame = () => {
  const colors = ['red', 'yellow', 'green', 'blue'];
  const numbers = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'];
  const actions = ['skip', 'reverse', '+2'];

  const createDeck = () => {
    const deck = [];
    colors.forEach(color => {
      // Un seul 0 par couleur
      deck.push({ color, value: '0', id: `${color}-0` });
      // Deux de chaque autre numéro
      for (let i = 1; i <= 9; i++) {
        deck.push({ color, value: i.toString(), id: `${color}-${i}-1` });
        deck.push({ color, value: i.toString(), id: `${color}-${i}-2` });
      }
      // Deux de chaque action par couleur
      actions.forEach(action => {
        deck.push({ color, value: action, id: `${color}-${action}-1` });
        deck.push({ color, value: action, id: `${color}-${action}-2` });
      });
    });
    // 4 jokers de chaque type
    for (let i = 0; i < 4; i++) {
      deck.push({ color: 'wild', value: 'wild', id: `wild-${i}` });
      deck.push({ color: 'wild', value: '+4', id: `wild+4-${i}` });
    }
    return deck.sort(() => Math.random() - 0.5);
  };

  const [deck, setDeck] = useState([]);
  const [playerHand, setPlayerHand] = useState([]);
  const [aiHand, setAiHand] = useState([]);
  const [discardPile, setDiscardPile] = useState([]);
  const [currentColor, setCurrentColor] = useState('');
  const [direction, setDirection] = useState(1);
  const [currentPlayer, setCurrentPlayer] = useState('player');
  const [gameStatus, setGameStatus] = useState('start');
  const [message, setMessage] = useState('');
  const [showColorPicker, setShowColorPicker] = useState(false);
  const [pendingWildCard, setPendingWildCard] = useState(null);
  const [playerSaidUno, setPlayerSaidUno] = useState(false);

  useEffect(() => {
    startNewGame();
  }, []);

  const startNewGame = () => {
    const newDeck = createDeck();
    const player = newDeck.splice(0, 7);
    const ai = newDeck.splice(0, 7);
    
    let firstCard = newDeck.pop();
    while (firstCard.color === 'wild' || firstCard.value === '+2' || firstCard.value === 'skip' || firstCard.value === 'reverse') {
      newDeck.unshift(firstCard);
      firstCard = newDeck.pop();
    }

    setDeck(newDeck);
    setPlayerHand(player);
    setAiHand(ai);
    setDiscardPile([firstCard]);
    setCurrentColor(firstCard.color);
    setCurrentPlayer('player');
    setGameStatus('playing');
    setMessage('À toi de jouer ! Clique une carte qui correspond à la couleur ou au numéro');
    setDirection(1);
    setPlayerSaidUno(false);
  };

  const canPlayCard = (card) => {
    const topCard = discardPile[discardPile.length - 1];
    
    if (card.color === 'wild') return true;
    if (card.color === currentColor) return true;
    if (card.value === topCard.value) return true;
    
    return false;
  };

  const hasPlayableCard = (hand) => {
    return hand.some(card => canPlayCard(card));
  };

  const handleCardClick = (card, index) => {
    if (currentPlayer !== 'player' || gameStatus !== 'playing') return;

    if (!canPlayCard(card)) {
      setMessage('❌ Cette carte ne correspond pas ! Choisis une carte de la même couleur ou du même numéro');
      return;
    }

    if (card.color === 'wild') {
      setPendingWildCard({ card, index });
      setShowColorPicker(true);
      return;
    }

    playPlayerCard(card, index, card.color);
  };

  const handleColorChoice = (chosenColor) => {
    if (!pendingWildCard) return;
    
    const { card, index } = pendingWildCard;
    setShowColorPicker(false);
    setPendingWildCard(null);
    playPlayerCard(card, index, chosenColor);
  };

  const playPlayerCard = (card, index, chosenColor) => {
    const newPlayerHand = [...playerHand];
    newPlayerHand.splice(index, 1);
    setPlayerHand(newPlayerHand);
    setDiscardPile([...discardPile, card]);
    setCurrentColor(chosenColor);
    setPlayerSaidUno(false);

    if (newPlayerHand.length === 1) {
      setMessage('🎯 N\'oublie pas de dire UNO !');
    }

    if (newPlayerHand.length === 0) {
      setGameStatus('win');
      setMessage('🎉 VICTOIRE ! Tu as gagné !');
      return;
    }

    applyCardEffect(card, 'ai', newPlayerHand);
  };

  const applyCardEffect = (card, nextPlayer, currentHand) => {
    if (card.value === 'skip') {
      setMessage(nextPlayer === 'ai' ? '⏭️ L\'IA passe son tour !' : '⏭️ Tu passes ton tour !');
      setTimeout(() => {
        if (nextPlayer === 'ai') {
          setCurrentPlayer('player');
          setMessage('À toi de jouer !');
        } else {
          aiTurn();
        }
      }, 1500);
    } else if (card.value === 'reverse') {
      setDirection(d => -d);
      setMessage('🔄 Sens inversé ! (Mais en 1v1, ça agit comme un Skip)');
      setTimeout(() => {
        if (nextPlayer === 'ai') {
          setCurrentPlayer('player');
          setMessage('À toi de jouer !');
        } else {
          aiTurn();
        }
      }, 1500);
    } else if (card.value === '+2') {
      setMessage(nextPlayer === 'ai' ? '📥 L\'IA pioche 2 cartes et passe son tour !' : '📥 Tu pioches 2 cartes et passes ton tour !');
      if (nextPlayer === 'ai') {
        drawCardsForPlayer('ai', 2);
        setTimeout(() => {
          setCurrentPlayer('player');
          setMessage('À toi de jouer !');
        }, 2000);
      } else {
        drawCardsForPlayer('player', 2);
        setTimeout(() => {
          aiTurn();
        }, 2000);
      }
    } else if (card.value === '+4') {
      setMessage(nextPlayer === 'ai' ? '📥 L\'IA pioche 4 cartes et passe son tour !' : '📥 Tu pioches 4 cartes et passes ton tour !');
      if (nextPlayer === 'ai') {
        drawCardsForPlayer('ai', 4);
        setTimeout(() => {
          setCurrentPlayer('player');
          setMessage('À toi de jouer !');
        }, 2000);
      } else {
        drawCardsForPlayer('player', 4);
        setTimeout(() => {
          aiTurn();
        }, 2000);
      }
    } else {
      setTimeout(() => {
        if (nextPlayer === 'ai') {
          aiTurn();
        } else {
          setCurrentPlayer('player');
          setMessage('À toi de jouer !');
        }
      }, 800);
    }
  };

  const drawCardsForPlayer = (player, count) => {
    let newDeck = [...deck];
    const drawn = [];
    
    for (let i = 0; i < count; i++) {
      if (newDeck.length === 0) {
        newDeck = reshuffleDeck();
      }
      if (newDeck.length > 0) {
        drawn.push(newDeck.pop());
      }
    }
    
    if (player === 'player') {
      setPlayerHand(prev => [...prev, ...drawn]);
    } else {
      setAiHand(prev => [...prev, ...drawn]);
    }
    
    setDeck(newDeck);
  };

  const reshuffleDeck = () => {
    if (discardPile.length <= 1) return [];
    const topCard = discardPile[discardPile.length - 1];
    const cardsToShuffle = discardPile.slice(0, -1);
    setDiscardPile([topCard]);
    return cardsToShuffle.sort(() => Math.random() - 0.5);
  };

  const handleDrawCard = () => {
    if (currentPlayer !== 'player' || gameStatus !== 'playing') return;
    
    let newDeck = [...deck];
    if (newDeck.length === 0) {
      newDeck = reshuffleDeck();
    }
    
    if (newDeck.length === 0) {
      setMessage('❌ Plus de cartes disponibles ! Passe ton tour');
      setTimeout(() => {
        setCurrentPlayer('ai');
        aiTurn();
      }, 1500);
      return;
    }

    const drawnCard = newDeck.pop();
    const newPlayerHand = [...playerHand, drawnCard];
    setPlayerHand(newPlayerHand);
    setDeck(newDeck);
    
    if (canPlayCard(drawnCard)) {
      setMessage('✅ Tu peux jouer la carte piochée ou passer ton tour');
      setTimeout(() => {
        if (currentPlayer === 'player') {
          setMessage('💡 Joue la carte piochée ou clique encore sur la pioche pour passer');
        }
      }, 2000);
    } else {
      setMessage('❌ La carte piochée ne peut pas être jouée. Tour de l\'IA...');
      setTimeout(() => {
        setCurrentPlayer('ai');
        aiTurn();
      }, 1500);
    }
  };

  const aiTurn = () => {
    setCurrentPlayer('ai');
    setMessage("🤖 L'IA réfléchit...");

    setTimeout(() => {
      const playableCards = aiHand.filter(card => canPlayCard(card));

      if (playableCards.length > 0) {
        // Stratégie IA simple: priorité aux cartes spéciales
        let cardToPlay = playableCards.find(c => c.value === '+4') ||
                         playableCards.find(c => c.value === '+2') ||
                         playableCards.find(c => c.value === 'skip') ||
                         playableCards.find(c => c.value === 'reverse') ||
                         playableCards.find(c => c.value === 'wild') ||
                         playableCards[0];

        const cardIndex = aiHand.findIndex(c => c.id === cardToPlay.id);
        const newAiHand = [...aiHand];
        newAiHand.splice(cardIndex, 1);
        setAiHand(newAiHand);
        setDiscardPile(prev => [...prev, cardToPlay]);

        let chosenColor = cardToPlay.color;
        if (cardToPlay.color === 'wild') {
          // L'IA choisit la couleur qu'elle a le plus
          const colorCounts = colors.map(c => 
            newAiHand.filter(card => card.color === c).length
          );
          const maxCount = Math.max(...colorCounts);
          chosenColor = colors[colorCounts.indexOf(maxCount)] || 'red';
        }
        
        setCurrentColor(chosenColor);
        
        const cardName = cardToPlay.value === 'wild' ? '🎨 Joker' : 
                        cardToPlay.value === '+4' ? '🎨 +4' :
                        cardToPlay.value;
        setMessage(`L'IA joue: ${cardName}${cardToPlay.color === 'wild' ? ` → ${chosenColor}` : ''}`);

        if (newAiHand.length === 1) {
          setMessage(`L'IA dit: UNO ! 😱`);
        }

        if (newAiHand.length === 0) {
          setGameStatus('lose');
          setMessage("😔 L'IA a gagné ! Revanche ?");
          return;
        }

        setTimeout(() => {
          applyCardEffect(cardToPlay, 'player', newAiHand);
        }, 1000);
      } else {
        // L'IA doit piocher
        let newDeck = [...deck];
        if (newDeck.length === 0) {
          newDeck = reshuffleDeck();
        }

        if (newDeck.length > 0) {
          const drawnCard = newDeck.pop();
          const newAiHand = [...aiHand, drawnCard];
          setAiHand(newAiHand);
          setDeck(newDeck);
          setMessage("L'IA pioche une carte...");
          
          // L'IA peut jouer la carte piochée si possible
          setTimeout(() => {
            if (canPlayCard(drawnCard)) {
              const updatedAiHand = newAiHand.filter(c => c.id !== drawnCard.id);
              setAiHand(updatedAiHand);
              setDiscardPile(prev => [...prev, drawnCard]);
              
              let chosenColor = drawnCard.color;
              if (drawnCard.color === 'wild') {
                const colorCounts = colors.map(c => 
                  updatedAiHand.filter(card => card.color === c).length
                );
                const maxCount = Math.max(...colorCounts);
                chosenColor = colors[colorCounts.indexOf(maxCount)] || 'red';
              }
              
              setCurrentColor(chosenColor);
              setMessage(`L'IA joue la carte piochée !`);
              
              setTimeout(() => {
                applyCardEffect(drawnCard, 'player', updatedAiHand);
              }, 1000);
            } else {
              setMessage("L'IA ne peut pas jouer, elle passe son tour");
              setTimeout(() => {
                setCurrentPlayer('player');
                setMessage('À toi de jouer !');
              }, 1500);
            }
          }, 1500);
        } else {
          setMessage("L'IA passe son tour");
          setTimeout(() => {
            setCurrentPlayer('player');
            setMessage('À toi de jouer !');
          }, 1500);
        }
      }
    }, 1500);
  };

  const getCardColor = (color) => {
    const colorMap = {
      red: 'bg-red-500',
      yellow: 'bg-yellow-400',
      green: 'bg-green-500',
      blue: 'bg-blue-500',
      wild: 'bg-gradient-to-br from-purple-600 via-pink-600 to-orange-600'
    };
    return colorMap[color] || 'bg-gray-500';
  };

  const getCardDisplay = (value) => {
    if (value === 'wild') return '🎨';
    if (value === '+4') return '🎨+4';
    if (value === 'skip') return '🚫';
    if (value === 'reverse') return '🔄';
    if (value === '+2') return '+2';
    return value;
  };

  const Card = ({ card, onClick, faceDown = false, highlight = false }) => (
    <div
      onClick={onClick}
      className={`relative w-20 h-28 rounded-xl shadow-lg cursor-pointer transform transition-all hover:scale-105 hover:-translate-y-2 ${
        faceDown ? 'bg-gradient-to-br from-gray-800 to-gray-900' : getCardColor(card.color)
      } flex items-center justify-center text-white font-bold text-2xl border-4 ${
        highlight ? 'border-yellow-300 animate-pulse' : 'border-white'
      }`}
    >
      {!faceDown && (
        <span className="drop-shadow-lg text-3xl">
          {getCardDisplay(card.value)}
        </span>
      )}
      {faceDown && <span className="text-4xl">🎴</span>}
    </div>
  );

  return (
    <div className="min-h-screen bg-gradient-to-br from-purple-900 via-purple-800 to-indigo-900 text-white p-4">
      <div className="max-w-6xl mx-auto">
        <div className="flex justify-between items-center mb-6">
          <h1 className="text-4xl font-bold">🎮 UNO Farcaster</h1>
          <button
            onClick={startNewGame}
            className="flex items-center gap-2 bg-white text-purple-900 px-4 py-2 rounded-lg font-semibold hover:bg-purple-100 transition-colors"
          >
            <RotateCw size={20} />
            Nouvelle partie
          </button>
        </div>

        <div className="bg-white/10 backdrop-blur-sm rounded-lg p-4 mb-6 text-center">
          <p className="text-xl font-semibold">{message}</p>
          <p className="text-sm mt-2">Pioche: {deck.length} cartes | Direction: {direction === 1 ? '→' : '←'}</p>
        </div>

        <div className="mb-8">
          <h2 className="text-xl mb-3 font-semibold flex items-center gap-2">
            🤖 IA 
            <span className="text-lg font-normal">({aiHand.length} cartes)</span>
            {aiHand.length === 1 && <span className="text-yellow-300 animate-bounce">UNO!</span>}
          </h2>
          <div className="flex gap-2 flex-wrap justify-center">
            {aiHand.map((card, i) => (
              <Card key={card.id} card={card} faceDown />
            ))}
          </div>
        </div>

        <div className="flex justify-center items-center gap-8 mb-8 bg-white/5 p-6 rounded-2xl">
          <div className="text-center">
            <p className="mb-2 text-sm font-semibold">PIOCHE</p>
            <Card card={{}} faceDown onClick={handleDrawCard} />
            <p className="mt-2 text-xs">Clique pour piocher</p>
          </div>
          
          <div className="text-center">
            <p className="mb-2 text-sm font-semibold">DERNIÈRE CARTE</p>
            {discardPile.length > 0 && (
              <div>
                <Card card={discardPile[discardPile.length - 1]} highlight={true} />
                <div className="mt-3 flex items-center justify-center gap-2">
                  <span className="text-sm font-semibold">Couleur active:</span>
                  <span className={`inline-block w-6 h-6 rounded-full ${getCardColor(currentColor)} border-2 border-white`}></span>
                </div>
              </div>
            )}
          </div>
        </div>

        <div>
          <h2 className="text-xl mb-3 font-semibold flex items-center gap-2">
            👤 Toi 
            <span className="text-lg font-normal">({playerHand.length} cartes)</span>
            {playerHand.length === 1 && <span className="text-yellow-300 animate-bounce">Dis UNO!</span>}
          </h2>
          <div className="flex gap-2 flex-wrap justify-center">
            {playerHand.map((card, i) => (
              <Card 
                key={card.id} 
                card={card} 
                onClick={() => handleCardClick(card, i)}
                highlight={canPlayCard(card) && currentPlayer === 'player'}
              />
            ))}
          </div>
        </div>

        {showColorPicker && (
          <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50">
            <div className="bg-white rounded-2xl p-8 text-gray-900">
              <h3 className="text-2xl font-bold mb-6 text-center">🎨 Choisis une couleur</h3>
              <div className="grid grid-cols-2 gap-4">
                {colors.map(color => (
                  <button
                    key={color}
                    onClick={() => handleColorChoice(color)}
                    className={`${getCardColor(color)} w-28 h-28 rounded-xl font-bold text-white text-xl hover:scale-110 transition-transform shadow-lg border-4 border-white`}
                  >
                    {color.toUpperCase()}
                  </button>
                ))}
              </div>
            </div>
          </div>
        )}

        {(gameStatus === 'win' || gameStatus === 'lose') && (
          <div className="fixed inset-0 bg-black/70 flex items-center justify-center z-50">
            <div className="bg-white rounded-2xl p-10 text-center text-gray-900 max-w-md">
              <h2 className="text-4xl font-bold mb-4">
                {gameStatus === 'win' ? '🎉 VICTOIRE !' : '😔 DÉFAITE'}
              </h2>
              <p className="text-xl mb-8">{message}</p>
              <button
                onClick={startNewGame}
                className="bg-purple-600 text-white px-8 py-4 rounded-xl font-semibold hover:bg-purple-700 transition-colors text-lg"
              >
                🔄 Rejouer
              </button>
            </div>
          </div>
        )}
      </div>
    </div>
  );
};

export default UnoGame;