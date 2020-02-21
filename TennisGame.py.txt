https://cyber-dojo.org/kata/edit/L0FbXg
TennisGame.py:

class TennisGame:
    pointNames = ["Love", "15", "30", "40"]

    def __init__(self):
        self.serverPoints = 0
        self.receiverPoints = 0
        
    def score(self):
        if ((self.serverPoints < 3) and (self.receiverPoints < 3) or \
            (self.serverPoints == 3) and (self.receiverPoints < 3) or \
            (self.serverPoints < 3) and (self.receiverPoints == 3)):
            return TennisGame.pointNames[self.serverPoints] + \
                " - " + \
                TennisGame.pointNames[self.receiverPoints]
            
        if (self.serverPoints == self.receiverPoints):
            return "Deuce"
            
        if ((3 < self.serverPoints) or (3 < self.receiverPoints)) and \
           (1 < abs(self.serverPoints - self.receiverPoints)):
            if (self.serverPoints > self.receiverPoints):
                return "Game Server"
            else:
                return "Game Receiver"
        
        if ((3 <= self.serverPoints) and (3 <= self.receiverPoints)):
            if (self.serverPoints > self.receiverPoints):
                return "Advantage Server"
            else:
                return "Advantage Receiver"
        
        return "ARE YOU KIDDING ME!!"

    def serverScoresPoint(self):
        self.serverPoints += 1
        
    def receiverScoresPoint(self):
        self.receiverPoints += 1
