---
layout: page
title: Essence - Individual Results
---

```python
for i in range(50):
    print(desc_array[i])
    print(top3_each[i], '\n')
    image1 = jpg_dir + top3_each[i][0] + '.jpg'
    image2 = jpg_dir + top3_each[i][1] + '.jpg'
    image3 = jpg_dir + top3_each[i][2] + '.jpg'
    output = '../EssenceOutputs-individual/essence-' + str(i) + '.jpg'
    display(HTML("<table><tr><td><img src='"+ image1 + "'></td><td><img src='" + image2 + "'></td><td><img src='"+ image3 + "'></td><td></td><td><img src='"+ output + "'></td></tr></table>"))
```

    ['Person 1', 'I am a 28-year-old woman living in Massachusetts.', "I'm neurotic and eccentric but good at heart.", 'I am obsessed with rabbits and love technology.']
    ['living', 'neurotic', 'obsessed'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/living.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/neurotic.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/obsessed.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-0.jpg'></td></tr></table>


    ['Person 2', 'I am dedicated and persistent and willing to go the extra mile', "i'm fun loving and like to make people laugh by telling jokes and making light of situations", 'I am insightful and am able to fit together pieces to understand the big picture']
    ['extra', 'light', 'understand'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/extra.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/light.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/understand.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-1.jpg'></td></tr></table>


    ['Person 3', 'I am a feminist, a student, and a homosexual.', 'I am kind, nurturing, caring, and genuine.', 'My honesty, my loyalty, and my generosity make me me.']
    ['homosexual', 'genuine', 'loyalty'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/homosexual.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/genuine.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/loyalty.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-2.jpg'></td></tr></table>


    ['Person 4', "I'm an immigrant who became a citizen of the United States. I'm an American.", "I can be stubborn and stand-offish, but I still care very much about my friends and family. I'm a nerd about movies/tvshows/books. I love video games and prefer to stay home.", "I'm introverted, so I need time alone to recharge and recalibrate."]
    ['citizen', 'stubborn', 'alone'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/citizen.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/stubborn.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/alone.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-3.jpg'></td></tr></table>


    ['Person 5', "I'm a boring person", "I'm quiet and introspective.", 'I have deep wells of sorrow.']
    ['boring', 'introspective', 'sorrow'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/boring.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/introspective.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/sorrow.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-4.jpg'></td></tr></table>


    ['Person 6', 'I am a girl who lives in New York City in my twenties who is incredibly close with my family.', 'I am very social and outgoing.', 'I am outgoing and care tremendously about my friends.']
    ['city', 'social', 'outgoing'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/city.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/social.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/outgoing.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-5.jpg'></td></tr></table>


    ['Person 7', 'I am a mom of 3', 'I like R &B Music, Japanese Food, Pizza', 'I am sympathetic.']
    ['mom', 'japanese', 'sympathetic'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/mom.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/japanese.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/sympathetic.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-6.jpg'></td></tr></table>


    ['Person 8', 'I am a licensed counselor.', "I'm silly and funny.", "I'm fun and sarcastic a lot of the time."]
    ['licensed', 'silly', 'fun'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/licensed.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/silly.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/fun.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-7.jpg'></td></tr></table>


    ['Person 9', "I'm Jim, a 53 year old american man", "I'm forceful, happy, calm and occasionally grumpy with a touch of sarcasm.", "I'm a drivan dominant at work and play. My wife is essential to my life. I'd be lost without her grounding me."]
    ['american', 'sarcasm', 'essential'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/american.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/sarcasm.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/essential.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-8.jpg'></td></tr></table>


    ['Person 10', "I'm a fat, biracial bisexual woman.", "I'm a funny depressive--aren't all depressives a riot?", "I'm a boring drudge, not glamorous or fancy, but fairly dependable."]
    ['fat', 'depressive', 'fairly'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/fat.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/depressive.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/fairly.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-9.jpg'></td></tr></table>


    ['Person 11', 'I am an adventurous geeky skydiver', 'I am fun-loving and love life.', 'I am intelligent and caring.']
    ['adventurous', 'life', 'intelligent'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/adventurous.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/life.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/intelligent.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-10.jpg'></td></tr></table>


    ['Person 12', "I am a person who believes that honesty and integrity is very important in today's society and world.", 'I am a person who is warm and sensitive to the feelings of others.', 'I see myself as one who you can count when the chips are down.']
    ['honesty', 'feelings', 'count'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/honesty.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/feelings.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/count.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-11.jpg'></td></tr></table>


    ['Person 13', "I am shy from those whom I don't know yet energetic and caring to those whom I do know.", 'I am a very happy and appreciate all life equally.', 'God is an important part of who I am. He allows me to me loving to all creatures no matter how small.']
    ['know', 'equally', 'creatures'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/know.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/equally.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/creatures.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-12.jpg'></td></tr></table>


    ['Person 14', 'I am a human', 'I am curious and interested in urbanity', 'My passion for cities and culture']
    ['human', 'curious', 'cities'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/human.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/curious.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/cities.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-13.jpg'></td></tr></table>


    ['Person 15', 'I am a musician', 'i am very laidback, easy going and unbrainwashed.', 'Making music makes me tick.']
    ['musician', 'laidback', 'tick'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/musician.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/laidback.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/tick.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-14.jpg'></td></tr></table>


    ['Person 16', 'I am a middle aged woman.', 'I am easy-going, caring, and nurturing.', "My essence is that I care a great deal about others to the point that I don't take care of myself."]
    ['aged', 'nurturing', 'point'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/aged.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/nurturing.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/point.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-15.jpg'></td></tr></table>


    ['Person 17', 'A male human being with a kind and loving personality.', 'Video Games and food', 'Humble, Kind, Loving']
    ['personality', 'food', 'humble'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/personality.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/food.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/humble.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-16.jpg'></td></tr></table>


    ['Person 18', 'I am a mother, wife, and friend', 'I am like the shoulder you can cry on, or a listening ear.', 'My family makes me me!']
    ['friend', 'cry', 'family'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/friend.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/cry.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/family.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-17.jpg'></td></tr></table>


    ['Person 19', 'I am an "older" adult who is finally understanding what is important and not important in this life.', 'I am an outgoing, sensitive, fun, creative and active person.', "Family is the essence of what makes me me. Without them, I'd be at a total loss."]
    ['important', 'creative', 'loss'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/important.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/creative.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/loss.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-18.jpg'></td></tr></table>


    ['Person 20', "I'm a 30 year old married man with a 2 year old daughter.", "I'm hard working, determined, goal oriented, relaxed and down to earth.", 'My ability to get along well with almost anyone is what makes me Me.']
    ['year', 'working', 'ability'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/year.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/working.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/ability.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-19.jpg'></td></tr></table>


    ['Person 21', 'I am an untraditional college student who is employed full time.', "I am an agreeable person who doesn't like to be bothered with others.", 'I am an introvert who is happy to pass the time by myself.']
    ['employed', 'agreeable', 'introvert'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/employed.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/agreeable.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/introvert.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-20.jpg'></td></tr></table>


    ['Person 22', 'A courteous female', 'Friendly and full of energy.', 'Family is making me to smile and be happy.']
    ['courteous', 'energy', 'making'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/courteous.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/energy.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/making.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-21.jpg'></td></tr></table>


    ['Person 23', 'A 52 year old married woman', 'Fun, outgoing, and social.', 'I am always willing to lend a hand or give a listening ear.']
    ['married', 'social', 'lend'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/married.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/social.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/lend.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-22.jpg'></td></tr></table>


    ['Person 24', 'I am a 25 year old American woman', 'I am introverted but also very nice and like to learn a lot', 'I try to make other people around me happy and try to make the world a better place to live in']
    ['american', 'learn', 'try'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/american.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/learn.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/try.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-23.jpg'></td></tr></table>


    ['Person 25', 'I am a mom and a wife.', 'I am pretty boring and quiet.', 'My love for my husband.']
    ['mom', 'boring', 'husband'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/mom.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/boring.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/husband.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-24.jpg'></td></tr></table>


    ['Person 26', 'a 28 year old male', 'intellegent and shy', 'i like to think about everything']
    ['male', 'shy', 'everything'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/male.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/shy.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/everything.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-25.jpg'></td></tr></table>


    ['Person 27', 'an inquisitive person', 'friendly and approachable', 'a desire to always learn new things']
    ['inquisitive', 'approachable', 'new'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/inquisitive.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/approachable.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/new.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-26.jpg'></td></tr></table>


    ['Person 28', 'I am donald, I am a 25 year old married man, working full time as a social media manager.', 'I am a friendly person, I like the outdoors, and going on adventures with my friends and family.', 'I am warm hearted individual, I am very kind, I love everyone and try never to judge anyone, I put others before myself.']
    ['social', 'outdoors', 'put'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/social.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/outdoors.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/put.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-27.jpg'></td></tr></table>


    ['Person 29', "I'm an average guy. A father, husband, brother, employee and friend. I am much like any other guy.", "I'm pretty down to earth. I like to laugh and play video games but I can be serious when I need to be serious.", 'I think what makes me me is that I am very open-minded as a person. I believe in forming my own opinions rather than just taking things at face value. I like to learn and experience things rather than be told how things are.']
    ['guy', 'serious', 'things'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/guy.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/serious.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/things.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-28.jpg'></td></tr></table>


    ['Person 30', "I'm a man who loves his wife very much.", "I'm loyal, devoted and always trying to do best in order to support our family.", 'Faith and strong will to pursue my hopes and dreams makes me to push through the day.']
    ['loves', 'best', 'push'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/loves.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/best.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/push.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-29.jpg'></td></tr></table>


    ['Person 31', 'I am a 43 old mother of two young boys under 7. I am am only child. I will be married for 9years in june.', 'I am an honest person. I am very disorganized and tend to be a half full person. I am loyal.', 'I have been created by God and uniquely created . My life experiences have made me me.']
    ['young', 'person', 'created'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/young.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/person.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/created.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-30.jpg'></td></tr></table>


    ['Person 32', 'I am a woman, a wife, a mother of 4.', 'I am introverted, quiet, compassionate, impractical, prone to depression.', 'I love to write.']
    ['woman', 'impractical', 'write'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/woman.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/impractical.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/write.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-31.jpg'></td></tr></table>


    ['Person 33', "I'm a wife and mother of 5 children.", 'I am introverted, honest and generous.', 'My Catholic faith is a big part of who I am and how I live my life.']
    ['children', 'generous', 'catholic'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/children.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/generous.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/catholic.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-32.jpg'></td></tr></table>


    ['Person 34', 'im a strong independent person.', 'im kind and warm hearted.', 'my persoanility makes me who i am.']
    ['independent', 'hearted', 'personality'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/independent.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/hearted.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/personality.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-33.jpg'></td></tr></table>


    ['Person 35', "I'm a mom of 3 children.", 'I am an outgoing, fun person who likes to go out and be social.', 'I am sincere, honest, and a good friend.  I am caring to others, especially my close friends!']
    ['children', 'go', 'honest'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/children.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/go.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/honest.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-34.jpg'></td></tr></table>


    ['Person 36', 'Someone who is calm, peaceful and stays relaxed under pressure.', 'I am nice, kind and funny but usually quiet.', 'I am caring, and I feel the need to help others.']
    ['relaxed', 'usually', 'feel'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/relaxed.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/usually.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/feel.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-35.jpg'></td></tr></table>


    ['Person 37', "I'm a loving and caring mom.", 'Fun, original, happy', 'Me']
    ['caring', 'original', 'ability'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/caring.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/original.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/ability.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-36.jpg'></td></tr></table>


    ['Person 38', 'I am a teacher of ESL', 'I love my husband and our dog, and want to be a mom, even though we are currently struggling with a miscarriage after 2 years of infertility treatments.', 'Right now, humor and talking to my friends in my infertility support group, as well as hanging out and taking pictures of my dog and husband.']
    ['esl', 'even', 'hanging'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/esl.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/even.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/hanging.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-37.jpg'></td></tr></table>


    ['Person 39', "I'm a cat lover who's kind of weird, but smart and funny.", "I'm relaxed and love animals.", 'I have kind of a weird take on things.']
    ['lover', 'animals', 'weird'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/lover.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/animals.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/weird.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-38.jpg'></td></tr></table>


    ['Person 40', 'i am a hard working smart female', 'im funny yet clever and warm', 'love for animals and others makes me who i am']
    ['hard', 'yet', 'animals'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/hard.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/yet.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/animals.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-39.jpg'></td></tr></table>


    ['Person 41', "I'm just a nice guy trying to be loving to others and find his way in the world.", "I'm nerdy, intelligent, and funny.", "I'm nobody special, but I do value my individuality and I love artistic expression."]
    ['trying', 'needy', 'expression'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/trying.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/needy.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/expression.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-40.jpg'></td></tr></table>


    ['Person 42', 'I am a wife, mother, and college student.', 'I am a loving, smart, fun, caring person . I love to sing, write, do crafts, art and whatever else I can do to help uplift others.', 'My personality and humor. But more importantly my big heart.']
    ['college', 'help', 'heart'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/college.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/help.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/heart.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-41.jpg'></td></tr></table>


    ['Person 43', 'I am funny.', 'I am easy going.', 'I have a great personality.']
    ['funny', 'easy', 'great'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/funny.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/easy.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/great.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-42.jpg'></td></tr></table>


    ['Person 44', 'henry johnson', 'stern,friendly,loving,strong of mind,family oriented,good worker,always looking forward within memories of the past', 'loving all the members of my faily,past and present']
    ['henry', 'memories', 'present'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/henry.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/memories.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/present.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-43.jpg'></td></tr></table>


    ['Person 45', 'I am a daughter, sister, friend, and advocate', "I advocate for those who don't have a voice", 'I care so deeply about children involved in the system and I will do almost anything to help them!']
    ['advocate', 'voice', 'deeply'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/advocate.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/voice.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/deeply.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-44.jpg'></td></tr></table>


    ['Person 46', 'I am a mom, wife, educator, sister, and daughter.', "I'm an introverted extrovert. I love to be on stage and the center of attention, but I hate small talk.", 'I am my own unique person who has never been known to follow a crowd.']
    ['educator', 'hate', 'known'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/educator.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/hate.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/known.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-45.jpg'></td></tr></table>


    ['Person 47', 'I am a mother, friend, and wife', 'I am active, adventurous, and hardwarling.', 'My values and principals.']
    ['friend', 'hardworking', 'values'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/friend.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/hardworking.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/values.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-46.jpg'></td></tr></table>


    ['Person 48', 'I am a soul that currently has the role of wife, mother, daughter, sister, and friend.', "I'm an introspective, introverted individual who cherishes both family time and alone time.", 'My quick wit, warm smile, and love of laughter make me who I am.']
    ['soul', 'time', 'laughter'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/soul.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/time.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/laughter.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-47.jpg'></td></tr></table>


    ['Person 49', 'I am a working mom.', 'I am calm, determined, and loving.', 'The essence of what makes me is my compassion and caring.']
    ['working', 'calm', 'compassion'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/working.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/calm.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/compassion.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-48.jpg'></td></tr></table>


    ['Person 50', 'I am a 27 year old special education teacher who lives in California.', 'I am a sociable and very goofy young guy who likes to make everyone laugh.', 'The essence of what makes me myself is that I am always generally positive and like to spread a smile to all those around me!']
    ['education', 'young', 'generally'] 
    



<table><tr><td><img src='../NounProjectOutputs/jpg_images/education.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/young.jpg'></td><td><img src='../NounProjectOutputs/jpg_images/generally.jpg'></td><td></td><td><img src='../EssenceOutputs-individual/essence-49.jpg'></td></tr></table>



```python

```