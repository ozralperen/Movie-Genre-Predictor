# Movie Genre Predictor from Synopsis

Goal of this project is to learn to use different natural language processing techniques and methods with neural networks. This project is a multilabel classifier that predicts multiple genres for a given movie synopsis.


## How The Code Will Be Run

Code file itself is saved as a notebook file to easily try different hyperparameters and parts of methods without the need of loading and/or processing the data to a point. This way user has the option to run the code on Google Colab with minimal additions to the code.
In either case, to train the model user needs a dataset that contains movie genres and synopsises in a certain format that will be explained under the **Dataset** subtitle.
User needs to install some Python libraries for the code to work properly. These libraries are Pandas, NLTK, Numpy, Tensorflow and Scikit-learn. You need to download necessary parts of NLTK seperately as well, pip won't be enough for the installation of NLTK. If you get any error, error will tell you the line of code you need to add to your code so it won't be hard. You can use nltk.download() to download necessary parts in an interactive interface.
Unfortunately trained model can't be saved and loaded properly, so users must train the model from scratch themselves.

## Dataset
Dataset must be kept under a subdirectory named data in the same directory as the code. This subdirectory must only contain movie files. Movie infos must be kept in a json file. Sharing the whole dataset is not allowed but to show the contents of the json file, here's an example that has 3 movies in it:

    {
    "data": [
	    {
	      "original_title": "Ariel",
	      "adult": false,
	      "id": 2,
	      "overview": "Taisto Kasurinen is a Finnish coal miner whose father has just committed suicide and who is framed for a crime he did not commit. In jail, he starts to dream about leaving the country and starting a new life. He escapes from prison but things don't go as planned...",
	      "tagline": "",
	      "title": "Ariel",
	      "genres": [
	        "Drama",
	        "Crime",
	        "Comedy"
	      ]
	    },
	    {
	      "original_title": "Varjoja paratiisissa",
	      "adult": false,
	      "id": 3,
	      "overview": "An episode in the life of Nikander, a garbage man, involving the death of a co-worker, an affair and much more.",
	      "tagline": "",
	      "title": "Shadows in Paradise",
	      "genres": [
	        "Drama",
	        "Comedy"
	      ]
	    },
	    {
	      "original_title": "Der freie Wille",
	      "adult": false,
	      "id": 9999,
	      "overview": "After nine years in psychiatric detention Theo, who has brutally assaulted and raped three women, is released. Living in a supervised community, he connects well with his social worker Sascha, finds a job at a print shop and even a girlfriend, Nettie, his principal's brittle and estranged daughter. But even though superficially everything seems to work out Theo's seething rage remains ready to erupt.",
	      "tagline": "",
	      "title": "The Free Will",
	      "genres": [
	        "Crime",
	        "Drama"
	      ]
	    }
	  ]
    }

 
Dataset itself consists of 100000 different movies. When we eleminate the ones that does not have a synopsis or genre tags, we are left with 60893 movies. 85% of this will be used for training and 15% will be used for testing. Each movie is labeled with one or multiple movie genres. There are 18 different movie genres in total: action, adventure, animation, comedy, crime, documentary, drama, family, fantasy, history, horror, music, mystery, romance, science fiction, tv movie, thriller, war, western.


## Model Accuracy and Alternatives

To find the most accurate model lots of different models and hyperparameters are tried. Best model found is included in the code. Another alternative is to use a GlobalMaxPooling instead of the convolutional and pooling layers. This eleminates flatten layer as well. It does 2% worse than the current model.
Current model's success is calculated by its recall, precision and f1 score. This rates vary in various runs up to %3. Last run gave results as: Precision: 0.4849, Recall: 0.6004, F1-measure: 0.5365. F1 score went up to 0.5615.
After running the code, user can try the system for themselves. Here are a few example synopsises and their outputs:
| Synopsis | True Genres | Predicted Genres|  
|--|--|--|
| A young programmer is selected to participate in a ground-breaking experiment in synthetic intelligence by evaluating the human qualities of a highly advanced humanoid A.I.| Drama, Sci-Fi, Thriller |'Science Fiction', 'Horror'
| In a near future, a lonely writer develops an unlikely relationship with an operating system designed to meet his every need.| Drama, Romance, Sci-Fi |'Drama', 'Comedy', 'Romance'
| During World War II, the English mathematical genius Alan Turing tries to crack the German Enigma code with help from fellow mathematicians.| Biography, Drama, Thriller |'Drama', 'War', 'History'
| In 19th-century France, Jean Valjean, who for decades has been hunted by the ruthless policeman Javert after breaking parole, agrees to care for a factory worker's daughter. The decision changes their lives forever.| Drama, History, Musical |'Drama'
| While navigating their careers in Los Angeles, a pianist and an actress fall in love while attempting to reconcile their aspirations for the future.| Comedy, Drama, Music |'Drama', 'Comedy', 'Romance'
| An unpublished writer returns to his hometown after graduating, where he seeks sponsors to publish his book while dealing with his father's deteriorating indulgence into gambling.| Drama |'Drama', 'Comedy', 'Romance'
| What if a child from another world crash-landed on Earth, but instead of becoming a hero to mankind, he proved to be something far more sinister?| Drama, Horror, Mystery |'Science Fiction', 'Horror'
| John Wick is on the run after killing a member of the international assassins' guild, and with a $14 million price tag on his head, he is the target of hit men and women everywhere.| Action, Crime, Thriller |'Crime', 'Action', 'Thriller'
| A family heads to an isolated hotel for the winter where a sinister presence influences the father into violence, while his psychic son sees horrific forebodings from both past and future.| Drama, Horror|'Thriller', 'Horror'
