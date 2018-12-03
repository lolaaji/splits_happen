input = 'XXXXXXXXXXX'



# scores from the actual rolls
point_scores = []
specials = []
previous = 0
for elem in input:
    if elem != ' ':
        if elem == 'X': # strike
            point_scores.append(10)
            specials.append('X')
        elif elem == '/': # spare
            point_scores.append(10-previous)
            specials.append('/')
        elif elem == '-': # gutter:
            point_scores.append(0)
            previous = 0
            specials.append('.')
        else: # pins
            point_scores.append(int(elem))
            previous = int(elem)
            specials.append('.')

# bonus scores from future rolls
bonus_scores = []
point_scores_len = len(point_scores)
for i in range(point_scores_len):
    if specials[i] == 'X':
        if i == point_scores_len-2: # second to last roll
            bonus_scores.append(point_scores[i+1])
        elif i == point_scores_len-1: # last roll
            bonus_scores.append(0)
        else: # all other rolls
            bonus_scores.append(point_scores[i+1]+point_scores[i+2])
    elif specials[i] == '/': # last roll is never a spare
        bonus_scores.append(point_scores[i+1])
    else:
        bonus_scores.append(0)

# add up the two kinds of scores
score = 0
for i in range(point_scores_len):
    score += point_scores[i]
    score += bonus_scores[i]

# if the last frame has three rolls, deduct the point_score from the last roll
input_split = input.split(' ')
if len(input_split[-1]) == 3:
    score -= point_scores[-1]

print('score: '+str(score))
