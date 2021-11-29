# Pima-Indian-Diabities
Pima indian diabities machine learning program Using KNN Algorithm . First You need to download csv file which is present on google and i have pasted here also. Write simple code and give proper path location where your csv file present . And use any python ide like jupyter notebook, spyder,.
 "import csv\n",
    "import math\n",
    "import random\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "def loadcsv(filename):\n",
    "    lines = csv.reader(open(r'C:\\Users\\Keytan\\Desktop\\macine learning/pima-indians-diabetes.data.csv'))\n",
    "    dataset =list(lines)\n",
    "    for i in range(len(dataset)):\n",
    "                            dataset[i] = [float(x) in dataset[i]]\n",
    "                            return dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "def splitDataset(dataset, splitRatio):\n",
    "    trainSize = int(len(dataset) * splitRatio)\n",
    "    trainSet = []\n",
    "    while len(trainSet) < trainSize:\n",
    "        index = random.randrange(len(copy))\n",
    "        trainSet.append(copy.pop(index))\n",
    "    return[trainSet, copy]    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [],
   "source": [
    "def separatedByClass(dataset):\n",
    "    separated = {}\n",
    "    for i in range(len(dataset)):\n",
    "        vector = dataset[i]\n",
    "        if(vector[-1] not in separated):\n",
    "            separated[vector[-1]] = []\n",
    "            separated[vector[-1]].append(vector)\n",
    "        return separated    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [],
   "source": [
    "def mean(numbers):\n",
    "    return sum(numbers)/float(len(numbers))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "def stdev(numbers):\n",
    "    avg = mean(numbers)\n",
    "    variance = sum([pow(x-avg,2) for x in numbers])/float(len(numbers)-1)\n",
    "    return math.sqrt(variance)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [],
   "source": [
    "def summarize(dataset):\n",
    "    summaries = [(mean(attribute), stdev(attribute)) for attribute in zip(*dataset)]\n",
    "    del summaries[-1]\n",
    "    return summaries\n",
    "    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [],
   "source": [
    "def smmarizedByClass(dataset):\n",
    "    separated = separatedByClass(dataset)\n",
    "    summaries = {}\n",
    "    for  classValue, instances in separated.items():\n",
    "        summaries[classValue] = summarize(instances)\n",
    "    return summaries"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [],
   "source": [
    "def calculateProbability(x, mean, stdev):\n",
    "    exponent = math.exp(-(math.pow(x-mean,2)/(2*math.pow(stdev,2))))\n",
    "    return (1/(math.sqrt(2*math.pi)*stdev))*exponent"
   ]
