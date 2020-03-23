from extensions import *
from helpers import product, maxXY, maxIdx, zeros
from graphlib import copyWG


def minPickDP(total:int, valueSet:Ints) -> int:
   """ Dynamic Programming Coin Change
   Returns min number of value picked from valueSet that = total
   """
   maxVal = product(valueSet)
   res = [0 for _ in range(total+1)]
   for i in range(1, total+1):
      res[i] = maxVal # to be replaced in if below if condition is true
      for val in valueSet:
         if i >= val and res[i - val] + 1 < res[i]:
            res[i] = res[i-val] + 1
   return res[total] if len(res) > total else 0

def manhattanTourist(Down:IntMat, Right:IntMat) -> int:
   """ 
   The Manhattan Tourist Problem
   Down:  downHt × (rightWd + 1) matrix
   Right: (downHt + 1) × rightWd matrix
   Returns length of a longest path from source (0, 0) to sink (n, m) in the rectangular grid
    whose edges are defined by the matrices Down and Right.
   """
   downHt = len(Down)
   rightWd = len(Right[0])
   if downHt+1 != len(Right):
      raise ValueError('manhattanTourist() -length (ht) of Down must be 1 < that of Right')
   if len(Down[0]) != rightWd+1:
      raise ValueError('manhattanTourist() -length of Down[0] (wd) must be 1 > that of Right')

   path = [[0 for i in range(rightWd+1)] for j in range(downHt+1)]
   for i in range(1, downHt+1):
      path[i][0] = path[i-1][0] + Down[i-1][0]
   for j in range(1, rightWd+1):
      path[0][j] = path[0][j-1] + Right[0][j-1]
   for i in range(1, downHt+1):
      for j in range(1, rightWd+1):
         path[i][j] = max(
            path[i-1][j] + Down[i-1][j],
            path[i][j-1] + Right[i][j-1],
         )      
   return path[downHt][rightWd]


Blosum62 = {'A': {'A': 4, 'C': 0, 'E': -1, 'D': -2, 'G': 0, 'F': -2, 'I': -1, 'H': -2, 'K': -1, 'M': -1, 'L': -1, 'N': -2, 'Q': -1, 'P': -1, 'S': 1, 'R': -1, 'T': 0, 'W': -3, 'V': 0, 'Y': -2}, 'C': {'A': 0, 'C': 9, 'E': -4, 'D': -3, 'G': -3, 'F': -2, 'I': -1, 'H': -3, 'K': -3, 'M': -1, 'L': -1, 'N': -3, 'Q': -3, 'P': -3, 'S': -1, 'R': -3, 'T': -1, 'W': -2, 'V': -1, 'Y': -2}, 'E': {'A': -1, 'C': -4, 'E': 5, 'D': 2, 'G': -2, 'F': -3, 'I': -3, 'H': 0, 'K': 1, 'M': -2, 'L': -3, 'N': 0, 'Q': 2, 'P': -1, 'S': 0, 'R': 0, 'T': -1, 'W': -3, 'V': -2, 'Y': -2}, 'D': {'A': -2, 'C': -3, 'E': 2, 'D': 6, 'G': -1, 'F': -3, 'I': -3, 'H': -1, 'K': -1, 'M': -3, 'L': -4, 'N': 1, 'Q': 0, 'P': -1, 'S': 0, 'R': -2, 'T': -1, 'W': -4, 'V': -3, 'Y': -3}, 'G': {'A': 0, 'C': -3, 'E': -2, 'D': -1, 'G': 6, 'F': -3, 'I': -4, 'H': -2, 'K': -2, 'M': -3, 'L': -4, 'N': 0, 'Q': -2, 'P': -2, 'S': 0, 'R': -2, 'T': -2, 'W': -2, 'V': -3, 'Y': -3}, 'F': {'A': -2, 'C': -2, 'E': -3, 'D': -3, 'G': -3, 'F': 6, 'I': 0, 'H': -1, 'K': -3, 'M': 0, 'L': 0, 'N': -3, 'Q': -3, 'P': -4, 'S': -2, 'R': -3, 'T': -2, 'W': 1, 'V': -1, 'Y': 3}, 'I': {'A': -1, 'C': -1, 'E': -3, 'D': -3, 'G': -4, 'F': 0, 'I': 4, 'H': -3, 'K': -3, 'M': 1, 'L': 2, 'N': -3, 'Q': -3, 'P': -3, 'S': -2, 'R': -3, 'T': -1, 'W': -3, 'V': 3, 'Y': -1}, 'H': {'A': -2, 'C': -3, 'E': 0, 'D': -1, 'G': -2, 'F': -1, 'I': -3, 'H': 8, 'K': -1, 'M': -2, 'L': -3, 'N': 1, 'Q': 0, 'P': -2, 'S': -1, 'R': 0, 'T': -2, 'W': -2, 'V': -3, 'Y': 2}, 'K': {'A': -1, 'C': -3, 'E': 1, 'D': -1, 'G': -2, 'F': -3, 'I': -3, 'H': -1, 'K': 5, 'M': -1, 'L': -2, 'N': 0, 'Q': 1, 'P': -1, 'S': 0, 'R': 2, 'T': -1, 'W': -3, 'V': -2, 'Y': -2}, 'M': {'A': -1, 'C': -1, 'E': -2, 'D': -3, 'G': -3, 'F': 0, 'I': 1, 'H': -2, 'K': -1, 'M': 5, 'L': 2, 'N': -2, 'Q': 0, 'P': -2, 'S': -1, 'R': -1, 'T': -1, 'W': -1, 'V': 1, 'Y': -1}, 'L': {'A': -1, 'C': -1, 'E': -3, 'D': -4, 'G': -4, 'F': 0, 'I': 2, 'H': -3, 'K': -2, 'M': 2, 'L': 4, 'N': -3, 'Q': -2, 'P': -3, 'S': -2, 'R': -2, 'T': -1, 'W': -2, 'V': 1, 'Y': -1}, 'N': {'A': -2, 'C': -3, 'E': 0, 'D': 1, 'G': 0, 'F': -3, 'I': -3, 'H': 1, 'K': 0, 'M': -2, 'L': -3, 'N': 6, 'Q': 0, 'P': -2, 'S': 1, 'R': 0, 'T': 0, 'W': -4, 'V': -3, 'Y': -2}, 'Q': {'A': -1, 'C': -3, 'E': 2, 'D': 0, 'G': -2, 'F': -3, 'I': -3, 'H': 0, 'K': 1, 'M': 0, 'L': -2, 'N': 0, 'Q': 5, 'P': -1, 'S': 0, 'R': 1, 'T': -1, 'W': -2, 'V': -2, 'Y': -1}, 'P': {'A': -1, 'C': -3, 'E': -1, 'D': -1, 'G': -2, 'F': -4, 'I': -3, 'H': -2, 'K': -1, 'M': -2, 'L': -3, 'N': -2, 'Q': -1, 'P': 7, 'S': -1, 'R': -2, 'T': -1, 'W': -4, 'V': -2, 'Y': -3}, 'S': {'A': 1, 'C': -1, 'E': 0, 'D': 0, 'G': 0, 'F': -2, 'I': -2, 'H': -1, 'K': 0, 'M': -1, 'L': -2, 'N': 1, 'Q': 0, 'P': -1, 'S': 4, 'R': -1, 'T': 1, 'W': -3, 'V': -2, 'Y': -2}, 'R': {'A': -1, 'C': -3, 'E': 0, 'D': -2, 'G': -2, 'F': -3, 'I': -3, 'H': 0, 'K': 2, 'M': -1, 'L': -2, 'N': 0, 'Q': 1, 'P': -2, 'S': -1, 'R': 5, 'T': -1, 'W': -3, 'V': -3, 'Y': -2}, 'T': {'A': 0, 'C': -1, 'E': -1, 'D': -1, 'G': -2, 'F': -2, 'I': -1, 'H': -2, 'K': -1, 'M': -1, 'L': -1, 'N': 0, 'Q': -1, 'P': -1, 'S': 1, 'R': -1, 'T': 5, 'W': -2, 'V': 0, 'Y': -2}, 'W': {'A': -3, 'C': -2, 'E': -3, 'D': -4, 'G': -2, 'F': 1, 'I': -3, 'H': -2, 'K': -3, 'M': -1, 'L': -2, 'N': -4, 'Q': -2, 'P': -4, 'S': -3, 'R': -3, 'T': -2, 'W': 11, 'V': -3, 'Y': 2}, 'V': {'A': 0, 'C': -1, 'E': -2, 'D': -3, 'G': -3, 'F': -1, 'I': 3, 'H': -3, 'K': -2, 'M': 1, 'L': 1, 'N': -3, 'Q': -2, 'P': -2, 'S': -2, 'R': -3, 'T': 0, 'W': -3, 'V': 4, 'Y': -1}, 'Y': {'A': -2, 'C': -2, 'E': -2, 'D': -3, 'G': -3, 'F': 3, 'I': -1, 'H': 2, 'K': -2, 'M': -1, 'L': -1, 'N': -2, 'Q': -1, 'P': -3, 'S': -2, 'R': -2, 'T': -2, 'W': 2, 'V': -1, 'Y': 7}}
Pam250   = {'A': {'A': 2, 'C': -2, 'E': 0, 'D': 0, 'G': 1, 'F': -3, 'I': -1, 'H': -1, 'K': -1, 'M': -1, 'L': -2, 'N': 0, 'Q': 0, 'P': 1, 'S': 1, 'R': -2, 'T': 1, 'W': -6, 'V': 0, 'Y': -3}, 'C': {'A': -2, 'C': 12, 'E': -5, 'D': -5, 'G': -3, 'F': -4, 'I': -2, 'H': -3, 'K': -5, 'M': -5, 'L': -6, 'N': -4, 'Q': -5, 'P': -3, 'S': 0, 'R': -4, 'T': -2, 'W': -8, 'V': -2, 'Y': 0}, 'E': {'A': 0, 'C': -5, 'E': 4, 'D': 3, 'G': 0, 'F': -5, 'I': -2, 'H': 1, 'K': 0, 'M': -2, 'L': -3, 'N': 1, 'Q': 2, 'P': -1, 'S': 0, 'R': -1, 'T': 0, 'W': -7, 'V': -2, 'Y': -4}, 'D': {'A': 0, 'C': -5, 'E': 3, 'D': 4, 'G': 1, 'F': -6, 'I': -2, 'H': 1, 'K': 0, 'M': -3, 'L': -4, 'N': 2, 'Q': 2, 'P': -1, 'S': 0, 'R': -1, 'T': 0, 'W': -7, 'V': -2, 'Y': -4}, 'G': {'A': 1, 'C': -3, 'E': 0, 'D': 1, 'G': 5, 'F': -5, 'I': -3, 'H': -2, 'K': -2, 'M': -3, 'L': -4, 'N': 0, 'Q': -1, 'P': 0, 'S': 1, 'R': -3, 'T': 0, 'W': -7, 'V': -1, 'Y': -5}, 'F': {'A': -3, 'C': -4, 'E': -5, 'D': -6, 'G': -5, 'F': 9, 'I': 1, 'H': -2, 'K': -5, 'M': 0, 'L': 2, 'N': -3, 'Q': -5, 'P': -5, 'S': -3, 'R': -4, 'T': -3, 'W': 0, 'V': -1, 'Y': 7}, 'I': {'A': -1, 'C': -2, 'E': -2, 'D': -2, 'G': -3, 'F': 1, 'I': 5, 'H': -2, 'K': -2, 'M': 2, 'L': 2, 'N': -2, 'Q': -2, 'P': -2, 'S': -1, 'R': -2, 'T': 0, 'W': -5, 'V': 4, 'Y': -1}, 'H': {'A': -1, 'C': -3, 'E': 1, 'D': 1, 'G': -2, 'F': -2, 'I': -2, 'H': 6, 'K': 0, 'M': -2, 'L': -2, 'N': 2, 'Q': 3, 'P': 0, 'S': -1, 'R': 2, 'T': -1, 'W': -3, 'V': -2, 'Y': 0}, 'K': {'A': -1, 'C': -5, 'E': 0, 'D': 0, 'G': -2, 'F': -5, 'I': -2, 'H': 0, 'K': 5, 'M': 0, 'L': -3, 'N': 1, 'Q': 1, 'P': -1, 'S': 0, 'R': 3, 'T': 0, 'W': -3, 'V': -2, 'Y': -4}, 'M': {'A': -1, 'C': -5, 'E': -2, 'D': -3, 'G': -3, 'F': 0, 'I': 2, 'H': -2, 'K': 0, 'M': 6, 'L': 4, 'N': -2, 'Q': -1, 'P': -2, 'S': -2, 'R': 0, 'T': -1, 'W': -4, 'V': 2, 'Y': -2}, 'L': {'A': -2, 'C': -6, 'E': -3, 'D': -4, 'G': -4, 'F': 2, 'I': 2, 'H': -2, 'K': -3, 'M': 4, 'L': 6, 'N': -3, 'Q': -2, 'P': -3, 'S': -3, 'R': -3, 'T': -2, 'W': -2, 'V': 2, 'Y': -1}, 'N': {'A': 0, 'C': -4, 'E': 1, 'D': 2, 'G': 0, 'F': -3, 'I': -2, 'H': 2, 'K': 1, 'M': -2, 'L': -3, 'N': 2, 'Q': 1, 'P': 0, 'S': 1, 'R': 0, 'T': 0, 'W': -4, 'V': -2, 'Y': -2}, 'Q': {'A': 0, 'C': -5, 'E': 2, 'D': 2, 'G': -1, 'F': -5, 'I': -2, 'H': 3, 'K': 1, 'M': -1, 'L': -2, 'N': 1, 'Q': 4, 'P': 0, 'S': -1, 'R': 1, 'T': -1, 'W': -5, 'V': -2, 'Y': -4}, 'P': {'A': 1, 'C': -3, 'E': -1, 'D': -1, 'G': 0, 'F': -5, 'I': -2, 'H': 0, 'K': -1, 'M': -2, 'L': -3, 'N': 0, 'Q': 0, 'P': 6, 'S': 1, 'R': 0, 'T': 0, 'W': -6, 'V': -1, 'Y': -5}, 'S': {'A': 1, 'C': 0, 'E': 0, 'D': 0, 'G': 1, 'F': -3, 'I': -1, 'H': -1, 'K': 0, 'M': -2, 'L': -3, 'N': 1, 'Q': -1, 'P': 1, 'S': 2, 'R': 0, 'T': 1, 'W': -2, 'V': -1, 'Y': -3}, 'R': {'A': -2, 'C': -4, 'E': -1, 'D': -1, 'G': -3, 'F': -4, 'I': -2, 'H': 2, 'K': 3, 'M': 0, 'L': -3, 'N': 0, 'Q': 1, 'P': 0, 'S': 0, 'R': 6, 'T': -1, 'W': 2, 'V': -2, 'Y': -4}, 'T': {'A': 1, 'C': -2, 'E': 0, 'D': 0, 'G': 0, 'F': -3, 'I': 0, 'H': -1, 'K': 0, 'M': -1, 'L': -2, 'N': 0, 'Q': -1, 'P': 0, 'S': 1, 'R': -1, 'T': 3, 'W': -5, 'V': 0, 'Y': -3}, 'W': {'A': -6, 'C': -8, 'E': -7, 'D': -7, 'G': -7, 'F': 0, 'I': -5, 'H': -3, 'K': -3, 'M': -4, 'L': -2, 'N': -4, 'Q': -5, 'P': -6, 'S': -2, 'R': 2, 'T': -5, 'W': 17, 'V': -6, 'Y': 0}, 'V': {'A': 0, 'C': -2, 'E': -2, 'D': -2, 'G': -1, 'F': -1, 'I': 4, 'H': -2, 'K': -2, 'M': 2, 'L': 2, 'N': -2, 'Q': -2, 'P': -1, 'S': -1, 'R': -2, 'T': 0, 'W': -6, 'V': 4, 'Y': -2}, 'Y': {'A': -3, 'C': 0, 'E': -4, 'D': -4, 'G': -5, 'F': 7, 'I': -1, 'H': 0, 'K': -4, 'M': -2, 'L': -1, 'N': -2, 'Q': -4, 'P': -5, 'S': -3, 'R': -4, 'T': -3, 'W': 0, 'V': -2, 'Y': 10}}

def LCSBackTrack(v:str, w:str, penalty=0, method='', matchScore=1) -> tuple[StrMat, int, int, int]:
   """ Longest Common Subsequence Backtrack
   Returns Mat of Backtracking pointers (symbols)
   method - 'global', 'local', 'fit', 'overlap'
   matchScore - score for a match, used by fit & overlap
   """
   vLen, wLen = len(v), len(w)
   S = zeros(wLen+1, vLen+1) # scoring matrix
   res = [['' for i in range(wLen +1)] for j in range(vLen +1)]
   scoreLU = Blosum62 if method=='global' else Pam250 if method=='local' else ScoreMat()
   useLU = len(scoreLU) > 0

   if penalty != 0 and method=='global':
      for i in range(1, vLen +1):
         S[i][0] = S[i-1][0] - penalty
   if penalty != 0:
      for j in range(1, wLen +1):
         S[0][j] = S[0][j-1] - penalty
   for i in range(1, vLen +1):
      for j in range(1, wLen +1):
         LUadj = scoreLU[v[i-1]][w[j-1]] if useLU else 0 
         adj = 0
         if method in ('global', 'local'):
            adj = LUadj
         elif v[i-1]==w[j-1]:
            adj = matchScore
         elif method in ('fit', 'overlap'):
            adj = -penalty
         s1 = S[i-1][j] - penalty
         s2 = S[i][j-1] - penalty
         s3 = S[i-1][j-1] + adj
         s0 = 0 if method=='local' else s1
         S[i][j] = max([s0, s1, s2, s3])

         if   S[i][j] == 0 and method=='local':
            res[i][j] = '*'
         elif S[i][j] == s1:
            res[i][j] = '↓'
         elif S[i][j] == s2:
            res[i][j] = '→'
         elif S[i][j] == s3:
            res[i][j] = '↘'
   x, y = wLen, vLen
   if method=='local':
      x, y = maxXY(S, -1)
   elif method=='fit':
      x = wLen
      y = maxIdx([s[-1] for s in S], -1)
   elif method=='overlap':
      x = maxIdx(S[-1], -1)
      y = vLen
   return res, S[y][x], y, x


def editDistance(v:str, w:str) -> int:
   vLen, wLen = len(v), len(w)
   S = zeros(wLen+1, vLen+1) # scoring matrix
   for i in range(1, vLen+1):
      S[i][0] = S[i-1][0  ] + 1
   for j in range(1, wLen+1):
      S[0][j] = S[0  ][j-1] + 1
   for i in range(1, vLen+1):
      for j in range(1, wLen+1):
         S[i][j] = min([
            S[i-1][j  ] + 1,
            S[i  ][j-1] + 1,
            S[i-1][j-1] + 1 if v[i-1] != w[j-1] else S[i-1][j-1]
         ])
   return S[vLen][wLen]

def recLCS(backtrack:StrMat, s:str, i:int, j:int) -> str:
   """ Eg.
   s: 'A ACCT TGG'
   w: 'ACAC TGTGA'
   r: 'A AC T TG ' = AACTTG.  Return stack ('-' is has matched return from else):
   - A
   > A
   - AA
   - AAC
   v AAC
   - AACT
   > AACT
   - AACTT
   - AACTTG
   > AACTTG
   v AACTTG
   """
   if i==0 or j==0:
      return ''
   elif backtrack[i][j] == '↓':
      return recLCS(backtrack, s, i-1, j)
   elif backtrack[i][j] == '→':
      return recLCS(backtrack, s, i,   j-1)
   else: # ↘
      return recLCS(backtrack, s, i-1, j-1) + s[i-1]

def getLCS(backtrack:StrMat, v:str, w:str, i:int, j:int, method:str) -> Strs:
   s1 = ''
   s2 = ''
   while i>0 and j>0:
      if backtrack[i][j] == '↓':
         s1 += v[i-1]
         s2 += '-'
         i -= 1
      elif backtrack[i][j] == '→':
         s1 += '-'
         s2 += w[j-1]
         j -= 1
      elif backtrack[i][j] == '↘':
         s1 += v[i-1]
         s2 += w[j-1]
         i -= 1
         j -= 1
      else: # *
         break
   if method=='global':
      while i>0:
         s1 += v[i-1]
         s2 += '-'
         i -= 1
      while j>0:
         s1 += '-'
         s2 += w[j-1]
         j -= 1
   return [s1[::-1], s2[::-1]]

def longestCommonSubseq(seq1:str, seq2:str) -> str:
   """ good tutorial: http://wordaligned.org/articles/longest-common-subsequence
   """
   backtrack, score, y, x = LCSBackTrack(seq1, seq2)
   return recLCS(backtrack, seq1, len(seq1), len(seq2))

def globalAlignment(v:str, w:str, penalty=5) -> tuple[int, Strs]:
   backtrack, score, y, x = LCSBackTrack(v, w, penalty, 'global')
   strs = getLCS(backtrack, v, w, len(v), len(w), 'global')
   return score, strs

def localAlignment(v:str, w:str, penalty=5) -> tuple[int, Strs]:
   backtrack, score, y, x = LCSBackTrack(v, w, penalty, 'local')
   strs = getLCS(backtrack, v, w, y, x, 'local')
   return score, strs

def fitAlignment(v:str, w:str, penalty=1) -> tuple[int, Strs]:
   backtrack, score, y, x = LCSBackTrack(v, w, penalty, 'fit')
   strs = getLCS(backtrack, v, w, y, x, 'fit')
   return score, strs

def overlapAlignment(v:str, w:str, penalty=2) -> tuple[int, Strs]:
   backtrack, score, y, x = LCSBackTrack(v, w, penalty, 'overlap')
   strs = getLCS(backtrack, v, w, y, x, 'overlap')
   return score, strs


def topologicalSort(wg:WGraph) -> WPaths:
   """ Sorts weighted graph from shortest to longest
   Eg.: [
      (0, [(1, 1), (3, 10)])]
      (1, [(2, 1)]),
      (2, [(3, 1)]),
   ] => 0 with 2 edges will be last
   """
   visited = WPaths()
   unvisited = copyWG(wg)
   while len(list(unvisited.keys())) > 0:
      cyclic = True
      for src, edges in unvisited.items():
         # src in loop from Eg.: 0, 1, 2, 0, 1, 0
         cyclicable = any([dst in unvisited for dst, _ in edges]) 
         if not cyclicable:
            # when:
            #  src=2: 3 not in unvisited
            #  src=1: 2 not in unvisited after 2 is removed from unvisited
            #  src=0: 1,3 not in unvisited after 1 is removed from unvisited
            cyclic = False
            del unvisited[src]
            visited.append((src, edges))
      if cyclic:
         raise ValueError("Graph is cyclic, not a DAG")
   return visited

def longestWeightedPath(sortedWtPaths:WPaths, source:str) -> tuple[int, Strs]:
   """ Returns the longest weighted DAG path from source in graph defined by sortedWtPaths
   """
   lens = dict[str, int]()
   paths = dict[str, Strs]()
   for src, edges in sortedWtPaths:
      lens[src] = 0
      paths[src] = Strs()
      for dst, wt in edges:
         lens[dst] = 0 if dst not in lens else lens[dst]
         paths[dst] = Strs() if dst not in paths else paths[dst]
         if lens[src] < lens[dst] + wt:
            lens[src] = lens[dst] + wt
            paths[src] = [dst] + paths[dst]
   return lens[source], [source]+paths[source]
