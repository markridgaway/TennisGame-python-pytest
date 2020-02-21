https://cyber-dojo.org/kata/edit/L0FbXg
test_TennisGame.py:

import TennisGame

def test_love_love_score():
    # Arrange
    game = TennisGame.TennisGame()
    
    # Act
    score = game.score()
    
    # Asert
    assert score == "Love - Love"
    
def test_server_scores_a_point():
    # Arrange
    game = TennisGame.TennisGame()
    originalServerPoints = game.serverPoints
    
    # Act
    game.serverScoresPoint()
    
    # Assert
    assert game.serverPoints == originalServerPoints + 1
    
def test_15_love_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "15 - Love"

def test_receiver_scores_a_point():
    # Arrange
    game = TennisGame.TennisGame()
    originalReceiverPoints = game.receiverPoints
    
    # Act
    game.receiverScoresPoint()
    
    # Assert
    assert game.receiverPoints == originalReceiverPoints + 1
    
def test_love_15_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.receiverScoresPoint()
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "Love - 15"

def test_30_30_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.receiverScoresPoint()
    game.receiverScoresPoint()
    game.serverScoresPoint()
    game.serverScoresPoint()
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "30 - 30"

def test_40_30_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()
    game.serverScoresPoint()
    game.serverScoresPoint()
    game.receiverScoresPoint()
    game.receiverScoresPoint()
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "40 - 30"

def test_30_40_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.receiverScoresPoint()
    game.receiverScoresPoint()
    game.receiverScoresPoint()
    game.serverScoresPoint()
    game.serverScoresPoint()
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "30 - 40"

def test_deuce_score():
    # Arrange
    game = TennisGame.TennisGame()
    game.receiverScoresPoint()  # Love - 15
    game.receiverScoresPoint()  # Love - 30
    game.serverScoresPoint()    # 15 - 30
    game.serverScoresPoint()    # 30 - 30
    game.receiverScoresPoint()  # 40 - 30
    game.serverScoresPoint()    # 40 - 40 or Deuce
   
    # Act
    score = game.score()
    
    # Assert
    assert score == "Deuce"
    
def test_game_server_before_deuce():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()
    game.serverScoresPoint()
    game.serverScoresPoint()
    game.serverScoresPoint()
    game.receiverScoresPoint()
    game.receiverScoresPoint()

    # Act
    score = game.score()
    
    # Assert
    assert score == "Game Server"
    
def test_game_server_after_deuce():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()    # 15 - Love
    game.serverScoresPoint()    # 30 - Love
    game.serverScoresPoint()    # 40 - Love
    game.receiverScoresPoint()  # 40 - 15
    game.receiverScoresPoint()  # 40 - 30
    game.receiverScoresPoint()  # Deuce
    game.serverScoresPoint()    # Advantage Server
    game.serverScoresPoint()    # Game Server

    # Act
    score = game.score()
    
    # Assert
    assert score == "Game Server"
    
def test_game_receiver_before_deuce():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()    # 15 - Love
    game.serverScoresPoint()    # 30 - Love
    game.receiverScoresPoint()  # 30 - 15
    game.receiverScoresPoint()  # 30 - 30
    game.receiverScoresPoint()  # 30 - 40
    game.receiverScoresPoint()  # Game Receiver

    # Act
    score = game.score()
    
    # Assert
    assert score == "Game Receiver"

def test_game_receiver_after_deuce():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()    # 15 - Love
    game.serverScoresPoint()    # 30 - Love
    game.receiverScoresPoint()  # 30 - 15
    game.receiverScoresPoint()  # 30 - 30
    game.receiverScoresPoint()  # 30 - 40
    game.serverScoresPoint()    # Deuce
    game.receiverScoresPoint()  # Advantage Receiver
    game.receiverScoresPoint()  # Game Receiver

    # Act
    score = game.score()
    
    # Assert
    assert score == "Game Receiver"

def test_advantage_server():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()    # 15 - Love
    game.serverScoresPoint()    # 30 - Love
    game.serverScoresPoint()    # 40 - Love
    game.receiverScoresPoint()  # 40 - 15
    game.receiverScoresPoint()  # 40 - 30
    game.receiverScoresPoint()  # Deuce
    game.serverScoresPoint()    # Advantage Server
    game.receiverScoresPoint()  # Deuce
    game.serverScoresPoint()    # Advantage Server
    
    # Act
    score = game.score()
    
    # Assert
    assert score == "Advantage Server"
    
def test_advantage_receiver():
    # Arrange
    game = TennisGame.TennisGame()
    game.serverScoresPoint()    # 15 - Love
    game.serverScoresPoint()    # 30 - Love
    game.receiverScoresPoint()  # 30 - 15
    game.receiverScoresPoint()  # 30 - 30
    game.receiverScoresPoint()  # 30 - 40
    game.serverScoresPoint()    # Deuce
    game.receiverScoresPoint()  # Advantage Receiver
    game.serverScoresPoint()    # Deuce
    game.receiverScoresPoint()  # Advantage Receiver

    # Act
    score = game.score()
    
    # Assert
    assert score == "Advantage Receiver"

