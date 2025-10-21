import React, { useState } from 'react';
import { Droplet, Skull, Heart, AlertTriangle, Wind, Edit2, ArrowUpDown, X, Camera, Calendar, BookOpen, ArrowLeft, Cake } from 'lucide-react';

export default function PlantGuiltCalculator() {
  const today = new Date().toISOString().split('T')[0];
  
  const [plants, setPlants] = useState([]);
  const [plantName, setPlantName] = useState('');
  const [plantType, setPlantType] = useState('pothos-water');
  const [lastCared, setLastCared] = useState(today);
  const [bornDate, setBornDate] = useState('');
  const [deleteConfirm, setDeleteConfirm] = useState(null);
  const [editingEmoji, setEditingEmoji] = useState(null);
  const [gardenOwner, setGardenOwner] = useState('');
  const [isEditingOwner, setIsEditingOwner] = useState(false);
  const [sortBy, setSortBy] = useState('urgency');
  const [selectedPlant, setSelectedPlant] = useState(null);
  const [newDiaryEntry, setNewDiaryEntry] = useState('');
  const [showBirthdayAlert, setShowBirthdayAlert] = useState(true);
  const [deletePhotoConfirm, setDeletePhotoConfirm] = useState(null);
  const [coverPhotoPosition, setCoverPhotoPosition] = useState(50);
  const [showPlantGuide, setShowPlantGuide] = useState(false);

  const plantNamePrefixes = ['Sir', 'Lady', 'Professor', 'Captain', 'Dr.', 'Duchess', 'Lord', 'Queen', 'King', 'Baron', 'Count', 'Princess'];
  const plantNameNouns = ['Sprout', 'Leafy', 'Greenie', 'Fern', 'Willow', 'Basil', 'Sage', 'Ivy', 'Clover', 'Moss', 'Root', 'Petal', 'Bloom', 'Thorn', 'Vine'];
  const plantNameSuffixes = ['the Magnificent', 'the Wise', 'the Bold', 'the Brave', 'the Gentle', 'von Plantenstein', 'McLeaf', 'the Third', 'Jr.', 'the Great', 'the Unstoppable'];

  const generateRandomName = () => {
    const plantInfo = plantDatabase[plantType];
    const isAirPlant = plantInfo.careType === 'mist';
    
    const airPlantNames = ['Aeris', 'Zephyr', 'Nimbus', 'Cirrus', 'Stratos', 'Mistral', 'Breeze'];
    const waterPlantNames = ['Aqua', 'Ripple', 'Splash', 'Hydro', 'Marina', 'Creek', 'River'];
    
    const specificName = isAirPlant 
      ? airPlantNames[Math.floor(Math.random() * airPlantNames.length)]
      : waterPlantNames[Math.floor(Math.random() * waterPlantNames.length)];
    
    const prefix = plantNamePrefixes[Math.floor(Math.random() * plantNamePrefixes.length)];
    const noun = Math.random() > 0.5 ? specificName : plantNameNouns[Math.floor(Math.random() * plantNameNouns.length)];
    const useSuffix = Math.random() > 0.5;
    const suffix = useSuffix ? ' ' + plantNameSuffixes[Math.floor(Math.random() * plantNameSuffixes.length)] : '';
    return `${prefix} ${noun}${suffix}`;
  };

  const plantDatabase = {
    'pothos-water': {
      name: 'Pothos (Water)',
      emoji: '🌿',
      careType: 'water',
      careDays: 7,
      careAction: 'change water',
      personality: 'chill',
      description: 'Change water every 7 days'
    },
    'lucky-bamboo': {
      name: 'Lucky Bamboo',
      emoji: '🎋',
      careType: 'water',
      careDays: 10,
      careAction: 'change water',
      personality: 'zen',
      description: 'Change water every 10 days'
    },
    'spider-plant-water': {
      name: 'Spider Plant (Water)',
      emoji: '🕷️',
      careType: 'water',
      careDays: 7,
      careAction: 'change water',
      personality: 'needy',
      description: 'Change water every 7 days'
    },
    'philodendron-water': {
      name: 'Philodendron (Water)',
      emoji: '🍃',
      careType: 'water',
      careDays: 7,
      careAction: 'change water',
      personality: 'dramatic',
      description: 'Change water every 7 days'
    },
    'coleus-water': {
      name: 'Coleus (Water)',
      emoji: '🌺',
      careType: 'water',
      careDays: 5,
      careAction: 'change water',
      personality: 'demanding',
      description: 'Change water every 5 days'
    },
    'mint-water': {
      name: 'Mint (Water)',
      emoji: '🌱',
      careType: 'water',
      careDays: 5,
      careAction: 'change water',
      personality: 'enthusiastic',
      description: 'Change water every 5 days'
    },
    'basil-water': {
      name: 'Basil (Water)',
      emoji: '🌿',
      careType: 'water',
      careDays: 5,
      careAction: 'change water',
      personality: 'dramatic',
      description: 'Change water every 5 days'
    },
    'sweet-potato-vine': {
      name: 'Sweet Potato Vine',
      emoji: '🍠',
      careType: 'water',
      careDays: 7,
      careAction: 'change water',
      personality: 'chill',
      description: 'Change water every 7 days'
    },
    'english-ivy-water': {
      name: 'English Ivy (Water)',
      emoji: '🌿',
      careType: 'water',
      careDays: 7,
      careAction: 'change water',
      personality: 'judgmental',
      description: 'Change water every 7 days'
    },
    'begonia-water': {
      name: 'Begonia (Water)',
      emoji: '🌸',
      careType: 'water',
      careDays: 5,
      careAction: 'change water',
      personality: 'demanding',
      description: 'Change water every 5 days'
    },
    'tillandsia-ionantha': {
      name: 'Tillandsia Ionantha',
      emoji: '🌵',
      careType: 'mist',
      careDays: 2,
      careAction: 'mist',
      personality: 'dramatic',
      description: 'Mist every 2-3 days'
    },
    'tillandsia-xerographica': {
      name: 'Tillandsia Xerographica',
      emoji: '🌀',
      careType: 'mist',
      careDays: 4,
      careAction: 'mist',
      personality: 'low-maintenance',
      description: 'Mist every 4-5 days'
    },
    'spanish-moss': {
      name: 'Spanish Moss',
      emoji: '🧶',
      careType: 'mist',
      careDays: 1,
      careAction: 'mist',
      personality: 'needy',
      description: 'Mist daily or soak weekly'
    },
    'tillandsia-bulbosa': {
      name: 'Tillandsia Bulbosa',
      emoji: '🐙',
      careType: 'mist',
      careDays: 3,
      careAction: 'mist',
      personality: 'chill',
      description: 'Mist every 3 days'
    },
    'tillandsia-caput-medusae': {
      name: 'Tillandsia Caput-Medusae',
      emoji: '🐍',
      careType: 'mist',
      careDays: 3,
      careAction: 'mist',
      personality: 'dramatic',
      description: 'Mist every 3 days'
    },
    'tillandsia-streptophylla': {
      name: 'Tillandsia Streptophylla',
      emoji: '🌀',
      careType: 'mist',
      careDays: 3,
      careAction: 'mist',
      personality: 'low-maintenance',
      description: 'Mist every 3-4 days'
    },
    'tillandsia-stricta': {
      name: 'Tillandsia Stricta',
      emoji: '💐',
      careType: 'mist',
      careDays: 2,
      careAction: 'mist',
      personality: 'needy',
      description: 'Mist every 2-3 days'
    },
    'tillandsia-tectorum': {
      name: 'Tillandsia Tectorum',
      emoji: '☁️',
      careType: 'mist',
      careDays: 5,
      careAction: 'mist',
      personality: 'low-maintenance',
      description: 'Mist every 5-7 days (fuzzy, drought-tolerant)'
    },
    'tillandsia-usneoides': {
      name: 'Tillandsia Usneoides',
      emoji: '🧵',
      careType: 'mist',
      careDays: 1,
      careAction: 'mist',
      personality: 'demanding',
      description: 'Mist daily'
    },
    'tillandsia-brachycaulos': {
      name: 'Tillandsia Brachycaulos',
      emoji: '🔥',
      careType: 'mist',
      careDays: 3,
      careAction: 'mist',
      personality: 'chill',
      description: 'Mist every 3 days'
    }
  };

  const getGuiltMessage = (daysOverdue, personality, careAction) => {
    const messages = {
      dramatic: {
        0: `Perfect timing! I'm living my best life! ✨`,
        1: `Getting a little thirsty over here...`,
        2: `Hello? Did you forget about me already?`,
        3: `I'm SUFFERING. This is plant abuse!`,
        5: `I can't believe you've done this. I literally can't.`,
        7: `Tell my roots I loved them. This is goodbye.`
      },
      chill: {
        0: `Hey, thanks for the ${careAction}! Appreciate it.`,
        1: `No rush, but I could use a ${careAction} soon.`,
        2: `Not to be dramatic, but it's been a while...`,
        3: `Okay, now I'm actually starting to feel it.`,
        5: `Dude. Seriously?`,
        7: `Even I have my limits, and you found them.`
      },
      needy: {
        0: `THANK YOU! You're the best plant parent ever! 💚`,
        1: `Already missing you... when's the next ${careAction}?`,
        2: `I know it hasn't been THAT long, but I'm getting worried...`,
        3: `ARE YOU SEEING SOMEONE ELSE? Another plant??`,
        5: `This is it. This is how I die. Abandoned.`,
        7: `I hope you're happy. I could've been THRIVING.`
      },
      judgmental: {
        0: `About time you remembered your responsibilities.`,
        1: `I see you've been busy. Too busy for plant care, apparently.`,
        2: `Your other plants are getting ${careAction}s. Just saying.`,
        3: `The audacity. The AUDACITY.`,
        5: `I'm taking notes. For when I write my memoir.`,
        7: `Congratulations on your complete failure as a plant parent.`
      },
      demanding: {
        0: `Finally! Was that so difficult?`,
        1: `I require MORE ATTENTION than this!`,
        2: `This is unacceptable. Truly unacceptable.`,
        3: `I demand to speak to your manager. Oh wait, that's you.`,
        5: `I'm filing a complaint with the Plant Protection Agency.`,
        7: `You're cut off. I'm going to live with someone who cares.`
      },
      'low-maintenance': {
        0: `Cool, thanks.`,
        1: `I'm good for now.`,
        2: `Could use a ${careAction} whenever you get a chance.`,
        3: `Not urgent, but... yeah, getting pretty dry here.`,
        5: `Okay, this is actually becoming a problem.`,
        7: `Even low-maintenance plants need SOME maintenance.`
      },
      zen: {
        0: `Balance restored. Peace achieved. 🧘`,
        1: `The natural cycle continues...`,
        2: `Patience wears thin, even for the enlightened.`,
        3: `Harmony disrupted. Chakras misaligned.`,
        5: `You have brought dishonor to this vessel.`,
        7: `My spirit departs. Namaste... goodbye.`
      },
      enthusiastic: {
        0: `YES! LET'S GO! I'M SO READY TO GROW!`,
        1: `Still feeling great! But let's keep this energy up!`,
        2: `Hey! HEY! Don't forget about me!`,
        3: `MY ENTHUSIASM IS DYING. IS THIS WHAT YOU WANT?`,
        5: `I was TRYING to be positive but you're making this HARD!`,
        7: `My spirit is broken. You broke my spirit.`
      }
    };

    const plantMessages = messages[personality];
    const thresholds = Object.keys(plantMessages).map(Number).sort((a, b) => a - b);
    
    for (let i = thresholds.length - 1; i >= 0; i--) {
      if (daysOverdue >= thresholds[i]) {
        return plantMessages[thresholds[i]];
      }
    }
    return plantMessages[0];
  };

  const getGuiltLevel = (daysOverdue) => {
    if (daysOverdue <= 0) return { level: 'thriving', color: 'bg-green-100 text-green-800', icon: Heart };
    if (daysOverdue <= 1) return { level: 'mild concern', color: 'bg-yellow-100 text-yellow-800', icon: AlertTriangle };
    if (daysOverdue <= 3) return { level: 'serious neglect', color: 'bg-orange-100 text-orange-800', icon: Droplet };
    return { level: 'PLANT CRISIS', color: 'bg-red-100 text-red-800', icon: Skull };
  };

  const addPlant = () => {
    if (plantName && lastCared) {
      const plantInfo = plantDatabase[plantType];
      const birthDate = bornDate ? new Date(bornDate) : null;
      
      setPlants([...plants, {
        id: Date.now(),
        name: plantName,
        type: plantType,
        lastCared: new Date(lastCared),
        bornDate: birthDate,
        plantInfo: plantInfo,
        emoji: plantInfo.emoji,
        coverPhoto: null,
        coverPhotoPosition: 50,
        photos: [],
        diary: []
      }]);
      setPlantName('');
      setLastCared(today);
      setBornDate('');
    }
  };

  const carePlant = (id) => {
    setPlants(plants.map(p => 
      p.id === id ? { ...p, lastCared: new Date() } : p
    ));
  };

  const confirmDelete = (id) => {
    setDeleteConfirm(id);
  };

  const deletePlant = (id) => {
    setPlants(plants.filter(p => p.id !== id));
    setDeleteConfirm(null);
    setSelectedPlant(null);
  };

  const cancelDelete = () => {
    setDeleteConfirm(null);
  };

  const updateEmoji = (id, newEmoji) => {
    setPlants(plants.map(p => 
      p.id === id ? { ...p, emoji: newEmoji } : p
    ));
    setEditingEmoji(null);
  };

  const handleCoverPhotoUpload = (e) => {
    const file = e.target.files[0];
    if (file) {
      const reader = new FileReader();
      reader.onloadend = () => {
        setPlants(plants.map(p => 
          p.id === selectedPlant.id ? { ...p, coverPhoto: reader.result, coverPhotoPosition: 50 } : p
        ));
      };
      reader.readAsDataURL(file);
    }
  };

  const updateCoverPhotoPosition = (position) => {
    setPlants(plants.map(p => 
      p.id === selectedPlant.id ? { ...p, coverPhotoPosition: position } : p
    ));
    setSelectedPlant(plants.find(p => p.id === selectedPlant.id) ? 
      { ...selectedPlant, coverPhotoPosition: position } : selectedPlant
    );
  };

  const deletePhoto = (photoIndex) => {
    setPlants(plants.map(p => 
      p.id === selectedPlant.id ? {
        ...p,
        photos: p.photos.filter((_, idx) => idx !== photoIndex)
      } : p
    ));
    setDeletePhotoConfirm(null);
  };

  const handlePhotoUpload = (e) => {
    const file = e.target.files[0];
    if (file) {
      const reader = new FileReader();
      reader.onloadend = () => {
        const note = prompt('Add a note for this photo (optional):');
        setPlants(plants.map(p => 
          p.id === selectedPlant.id ? { 
            ...p, 
            photos: [...p.photos, { url: reader.result, date: new Date(), note: note || '' }] 
          } : p
        ));
      };
      reader.readAsDataURL(file);
    }
  };

  const addDiaryEntry = () => {
    if (newDiaryEntry.trim()) {
      setPlants(plants.map(p => 
        p.id === selectedPlant.id ? { 
          ...p, 
          diary: [...p.diary, { text: newDiaryEntry, date: new Date() }] 
        } : p
      ));
      setNewDiaryEntry('');
    }
  };

  const getDaysOverdue = (lastCared, careDays) => {
    const now = new Date();
    const last = new Date(lastCared);
    const daysSinceCare = Math.floor((now - last) / (1000 * 60 * 60 * 24));
    return daysSinceCare - careDays;
  };

  const getDaysSinceCare = (lastCared) => {
    const now = new Date();
    const last = new Date(lastCared);
    return Math.floor((now - last) / (1000 * 60 * 60 * 24));
  };

  const getAge = (bornDate) => {
    if (!bornDate) return 'Unknown age';
    const now = new Date();
    const born = new Date(bornDate);
    const diffTime = Math.abs(now - born);
    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    
    if (diffDays < 30) return `${diffDays} days old`;
    if (diffDays < 365) return `${Math.floor(diffDays / 30)} months old`;
    const years = Math.floor(diffDays / 365);
    const months = Math.floor((diffDays % 365) / 30);
    return months > 0 ? `${years}y ${months}m old` : `${years} year${years > 1 ? 's' : ''} old`;
  };

  const getUpcomingBirthdays = () => {
    const today = new Date();
    const upcoming = plants.filter(plant => {
      if (!plant.bornDate) return false;
      const born = new Date(plant.bornDate);
      const thisYearBirthday = new Date(today.getFullYear(), born.getMonth(), born.getDate());
      const daysDiff = Math.ceil((thisYearBirthday - today) / (1000 * 60 * 60 * 24));
      return daysDiff >= 0 && daysDiff <= 7;
    });
    return upcoming;
  };

  const getSortedPlants = () => {
    const plantsWithStatus = plants.map(plant => {
      const daysOverdue = getDaysOverdue(plant.lastCared, plant.plantInfo.careDays);
      const daysSinceCare = getDaysSinceCare(plant.lastCared);
      const isWatered = daysOverdue <= 0;
      return { ...plant, daysOverdue, daysSinceCare, isWatered };
    });

    if (sortBy === 'urgency') {
      const wateredPlants = plantsWithStatus.filter(p => p.isWatered);
      const needsCare = plantsWithStatus.filter(p => !p.isWatered);
      const sortedNeeds = needsCare.sort((a, b) => b.daysOverdue - a.daysOverdue);
      return [...sortedNeeds, ...wateredPlants.sort((a, b) => new Date(b.lastCared) - new Date(a.lastCared))];
    } else if (sortBy === 'oldest') {
      return plantsWithStatus.sort((a, b) => new Date(a.lastCared) - new Date(b.lastCared));
    } else if (sortBy === 'newest') {
      return plantsWithStatus.sort((a, b) => new Date(b.lastCared) - new Date(a.lastCared));
    }
    return plantsWithStatus;
  };

  const upcomingBirthdays = getUpcomingBirthdays();

  if (selectedPlant) {
    const plant = plants.find(p => p.id === selectedPlant.id);
    if (!plant) {
      setSelectedPlant(null);
      return null;
    }

    const daysOverdue = getDaysOverdue(plant.lastCared, plant.plantInfo.careDays);
    const daysSinceCare = getDaysSinceCare(plant.lastCared);
    const isWatered = daysOverdue <= 0;
    const guiltStatus = getGuiltLevel(daysOverdue);
    const GuiltIcon = guiltStatus.icon;
    const message = getGuiltMessage(daysOverdue, plant.plantInfo.personality, plant.plantInfo.careAction);
    const CareIcon = plant.plantInfo.careType === 'mist' ? Wind : Droplet;

    return (
      <div className="min-h-screen bg-gradient-to-br from-green-50 to-emerald-100">
        {/* Cover Photo Section */}
        <div className="relative h-64 bg-gradient-to-r from-green-400 to-emerald-500 overflow-hidden">
          {plant.coverPhoto ? (
            <>
              <img 
                src={plant.coverPhoto} 
                alt="Cover" 
                className="w-full h-full object-cover" 
                style={{ objectPosition: `center ${plant.coverPhotoPosition || 50}%` }}
              />
              <div className="absolute bottom-4 right-4 bg-white rounded-lg p-2 shadow-lg">
                <label className="text-xs text-gray-600 block mb-1">Adjust Position</label>
                <input
                  type="range"
                  min="0"
                  max="100"
                  value={plant.coverPhotoPosition || 50}
                  onChange={(e) => updateCoverPhotoPosition(parseInt(e.target.value))}
                  className="w-32"
                />
              </div>
            </>
          ) : (
            <div className="w-full h-full flex items-center justify-center">
              <label className="cursor-pointer flex flex-col items-center text-white hover:text-green-100 transition">
                <Camera size={48} />
                <span className="mt-2">Add Cover Photo</span>
                <input type="file" accept="image/*" onChange={handleCoverPhotoUpload} className="hidden" />
              </label>
            </div>
          )}
          {plant.coverPhoto && (
            <label className="absolute top-4 right-4 bg-white rounded-full p-2 cursor-pointer hover:bg-gray-100 transition shadow-lg">
              <Camera size={20} />
              <input type="file" accept="image/*" onChange={handleCoverPhotoUpload} className="hidden" />
            </label>
          )}
          <button
            onClick={() => setSelectedPlant(null)}
            className="absolute top-4 left-4 bg-white rounded-full p-2 hover:bg-gray-100 transition shadow-lg"
          >
            <ArrowLeft size={20} />
          </button>
        </div>

        {/* Plant Header */}
        <div className="max-w-4xl mx-auto px-6 -mt-16 relative">
          <div className="bg-white rounded-lg shadow-xl p-6">
            <div className="flex items-start gap-4">
              <div className="relative -mt-20">
                <div className="bg-white rounded-lg p-3 shadow-lg">
                  {editingEmoji === plant.id ? (
                    <input
                      type="text"
                      value={plant.emoji}
                      onChange={(e) => updateEmoji(plant.id, e.target.value)}
                      onBlur={() => setEditingEmoji(null)}
                      maxLength="2"
                      autoFocus
                      className="text-6xl w-20 text-center border-2 border-green-500 rounded"
                    />
                  ) : (
                    <div className="relative group">
                      <span className="text-6xl">{plant.emoji}</span>
                      <button
                        onClick={() => setEditingEmoji(plant.id)}
                        className="absolute -top-1 -right-1 bg-green-500 text-white rounded-full p-1 opacity-0 group-hover:opacity-100 transition"
                      >
                        <Edit2 size={14} />
                      </button>
                    </div>
                  )}
                </div>
              </div>
              <div className="flex-1 pt-2">
                <h1 className="text-3xl font-bold text-green-900">{plant.name}</h1>
                <p className="text-lg text-green-600">{plant.plantInfo.name}</p>
                <p className="text-sm text-gray-500 mt-1">{plant.plantInfo.description}</p>
              </div>
              <div className="flex gap-2">
                <button
                  onClick={() => !isWatered && carePlant(plant.id)}
                  disabled={isWatered}
                  className={`px-4 py-2 rounded transition flex items-center gap-2 ${
                    isWatered
                      ? 'bg-gray-300 text-gray-500 cursor-not-allowed'
                      : 'bg-blue-500 text-white hover:bg-blue-600'
                  }`}
                >
                  <CareIcon size={16} /> 
                  {isWatered ? 'Watered ✓' : (plant.plantInfo.careType === 'mist' ? 'Mist Now' : 'Change Water')}
                </button>
              </div>
            </div>

            {/* Plant Stats */}
            <div className="grid grid-cols-3 gap-4 mt-6 pt-6 border-t">
              <div>
                <p className="text-sm text-gray-500">Born</p>
                {plant.bornDate ? (
                  <>
                    <p className="text-lg font-semibold text-gray-900">
                      {new Date(plant.bornDate).toLocaleDateString()}
                    </p>
                    <p className="text-sm text-green-600">{getAge(plant.bornDate)}</p>
                  </>
                ) : (
                  <p className="text-sm text-gray-400 italic">Date unknown</p>
                )}
              </div>
              <div>
                <p className="text-sm text-gray-500">Last Care</p>
                <p className="text-lg font-semibold text-gray-900">
                  {daysSinceCare} day{daysSinceCare !== 1 ? 's' : ''} ago
                </p>
                {daysOverdue > 0 ? (
                  <p className="text-sm text-red-600">{daysOverdue} day{daysOverdue !== 1 ? 's' : ''} overdue</p>
                ) : (
                  <p className="text-sm text-green-600">Next in {Math.abs(daysOverdue)} day{Math.abs(daysOverdue) !== 1 ? 's' : ''}</p>
                )}
              </div>
              <div>
                <p className="text-sm text-gray-500">Status</p>
                <span className={`inline-flex items-center gap-2 px-3 py-1 rounded-full text-sm font-medium ${guiltStatus.color}`}>
                  <GuiltIcon size={16} />
                  {guiltStatus.level}
                </span>
              </div>
            </div>

            {/* Guilt Message */}
            {!isWatered && (
              <div className="mt-6 bg-gray-50 rounded-lg p-4 italic text-gray-700 border-l-4 border-green-500">
                "{message}"
              </div>
            )}
          </div>

          {/* Photo Gallery & Diary Combined */}
          <div className="bg-white rounded-lg shadow-lg p-6 mt-6">
            <div className="flex items-center justify-between mb-4">
              <h2 className="text-xl font-semibold text-green-900 flex items-center gap-2">
                <Camera size={20} className="mb-0.5" />
                Plant Journal
              </h2>
              <label className="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700 transition cursor-pointer">
                Add Photo & Note
                <input type="file" accept="image/*" onChange={handlePhotoUpload} className="hidden" />
              </label>
            </div>
            {plant.photos.length === 0 ? (
              <p className="text-gray-500 text-center py-8">No journal entries yet. Start documenting your plant's story!</p>
            ) : (
              <div className="grid grid-cols-3 gap-4">
                {plant.photos.map((photo, idx) => (
                  <div key={idx} className="relative group">
                    <img src={photo.url} alt={`Entry ${idx + 1}`} className="w-full h-80 object-cover rounded-lg" />
                    <div className="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-black to-transparent text-white p-3 rounded-b-lg">
                      <p className="text-xs font-medium mb-1">{new Date(photo.date).toLocaleDateString()}</p>
                      {photo.note && <p className="text-sm italic line-clamp-2">{photo.note}</p>}
                    </div>
                    <div className="absolute top-2 right-2 flex gap-2 opacity-0 group-hover:opacity-100 transition">
                      <button
                        onClick={(e) => {
                          e.stopPropagation();
                          const currentPlant = plants.find(p => p.id === selectedPlant.id);
                          const note = prompt('Edit note for this photo:', currentPlant.photos[idx].note);
                          if (note !== null) {
                            setPlants(plants.map(p => 
                              p.id === selectedPlant.id ? {
                                ...p,
                                photos: p.photos.map((ph, i) => i === idx ? { ...ph, note } : ph)
                              } : p
                            ));
                          }
                        }}
                        className="bg-white text-gray-800 rounded-full p-2 shadow-lg hover:bg-gray-100"
                      >
                        <Edit2 size={16} />
                      </button>
                      <button
                        onClick={(e) => {
                          e.stopPropagation();
                          setDeletePhotoConfirm(idx);
                        }}
                        className="bg-red-500 text-white rounded-full p-2 shadow-lg hover:bg-red-600"
                      >
                        <X size={16} />
                      </button>
                    </div>
                  </div>
                ))}
              </div>
            )}
          </div>

          <div className="bg-blue-50 border-2 border-blue-300 rounded-lg p-6 mt-6 mb-6">
            <h3 className="text-lg font-semibold text-blue-900 mb-3">💡 Future Features (Roadmap)</h3>
            <p className="text-sm text-blue-800 mb-2">
              This prototype is memory-based only. Here's what we couldn't add but would be awesome:
            </p>
            <ul className="list-disc list-inside text-sm text-blue-700 space-y-1">
              <li><strong>Push Notifications:</strong> Get alerts on your phone for plant birthdays and overdue care</li>
              <li><strong>Persistent Storage:</strong> Save your plants, photos, and diary entries permanently (currently lost on refresh)</li>
              <li><strong>Future-Proof Dates:</strong> Update date blocking logic to always prevent future dates as time passes</li>
              <li><strong>Plant Guide with Photos:</strong> Visual guide showing all 20 plants with reference images</li>
              <li><strong>Edit Journal Notes:</strong> Inline editing for photo captions without popup prompts</li>
              <li><strong>Cover Photo Repositioning:</strong> Drag-to-adjust cover photo positioning with visual preview</li>
              <li><strong>Data Export:</strong> Download your plant journal as a PDF or backup file</li>
              <li><strong>Cloud Sync:</strong> Access your garden from any device</li>
              <li><strong>Reminders:</strong> Browser/phone notifications when care is needed</li>
            </ul>
            <p className="text-xs text-blue-600 mt-3 italic">
              📝 <strong>Design Note:</strong> Transparency boxes like this are great for consumer products! Shows what's being worked on, manages expectations, and builds trust. Could be dynamically updated with real roadmap data in production.
            </p>
          </div>

          {/* Delete Photo Confirmation Modal */}
          {deletePhotoConfirm !== null && (
            <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
              <div className="bg-white rounded-lg shadow-xl p-6 max-w-md mx-4">
                <h3 className="text-xl font-bold text-gray-900 mb-2">Delete This Memory? 📸</h3>
                <p className="text-gray-600 mb-6">
                  Are you sure you want to delete this photo and note? This can't be undone.
                </p>
                <div className="flex gap-3 justify-end">
                  <button
                    onClick={() => setDeletePhotoConfirm(null)}
                    className="px-4 py-2 bg-gray-200 text-gray-800 rounded hover:bg-gray-300 transition"
                  >
                    Cancel
                  </button>
                  <button
                    onClick={() => deletePhoto(deletePhotoConfirm)}
                    className="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600 transition"
                  >
                    Yes, Delete
                  </button>
                </div>
              </div>
            </div>
          )}

          {/* Plant Guide Modal */}
          {showPlantGuide && (
            <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4 overflow-y-auto">
              <div className="bg-white rounded-lg shadow-xl p-6 max-w-3xl w-full my-8">
                <div className="flex justify-between items-start mb-4">
                  <div>
                    <h3 className="text-2xl font-bold text-gray-900">Water & Air Plants Guide</h3>
                    <p className="text-sm text-gray-600 mt-1">Not all plants need soil to thrive!</p>
                  </div>
                  <button
                    onClick={() => setShowPlantGuide(false)}
                    className="text-gray-500 hover:text-gray-700"
                  >
                    <X size={24} />
                  </button>
                </div>

                <div className="mb-6">
                  <h4 className="font-semibold text-gray-900 mb-2">Why Water & Air Plants?</h4>
                  <ul className="text-sm text-gray-700 space-y-1 list-disc list-inside">
                    <li><strong>Low maintenance:</strong> No soil means no mess, perfect for apartments and small spaces</li>
                    <li><strong>Unique aesthetic:</strong> Display in glass containers, hanging terrariums, or creative vessels</li>
                    <li><strong>Cleaner air:</strong> Both types naturally purify indoor air</li>
                    <li><strong>Beginner-friendly:</strong> Hard to overwater, easier care schedules than soil plants</li>
                    <li><strong>Space-saving:</strong> Hang, mount, or display anywhere without pots</li>
                  </ul>
                </div>

                <h4 className="font-semibold text-gray-900 mb-3">Our Plant Library (20 Plants)</h4>
                
                <div className="mb-4">
                  <h5 className="font-medium text-green-800 mb-2">💧 Water-Grown Plants</h5>
                  <div className="grid grid-cols-2 gap-2 text-sm">
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌿 Pothos (Water)</span> - Change water every 7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🎋 Lucky Bamboo</span> - Change water every 10 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🕷️ Spider Plant</span> - Change water every 7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🍃 Philodendron</span> - Change water every 7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌺 Coleus</span> - Change water every 5 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌱 Mint</span> - Change water every 5 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌿 Basil</span> - Change water every 5 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🍠 Sweet Potato Vine</span> - Change water every 7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌿 English Ivy</span> - Change water every 7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌸 Begonia</span> - Change water every 5 days
                    </div>
                  </div>
                </div>

                <div>
                  <h5 className="font-medium text-green-800 mb-2">💨 Air Plants (Tillandsia)</h5>
                  <div className="grid grid-cols-2 gap-2 text-sm">
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌵 Tillandsia Ionantha</span> - Mist every 2-3 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌀 Tillandsia Xerographica</span> - Mist every 4-5 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🧶 Spanish Moss</span> - Mist daily
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🐙 Tillandsia Bulbosa</span> - Mist every 3 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🐍 Tillandsia Caput-Medusae</span> - Mist every 3 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🌀 Tillandsia Streptophylla</span> - Mist every 3-4 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">💐 Tillandsia Stricta</span> - Mist every 2-3 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">☁️ Tillandsia Tectorum</span> - Mist every 5-7 days
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🧵 Tillandsia Usneoides</span> - Mist daily
                    </div>
                    <div className="border border-gray-200 rounded p-2">
                      <span className="font-medium">🔥 Tillandsia Brachycaulos</span> - Mist every 3 days
                    </div>
                  </div>
                </div>

                <button
                  onClick={() => setShowPlantGuide(false)}
                  className="mt-6 w-full bg-green-600 text-white py-2 rounded hover:bg-green-700 transition"
                >
                  Got it!
                </button>
              </div>
            </div>
          )}
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-gradient-to-br from-green-50 to-emerald-100 p-6">
      <div className="max-w-4xl mx-auto">
        <div className="text-center mb-8">
          {isEditingOwner ? (
            <div className="flex items-center justify-center gap-2 mb-2">
              <input
                type="text"
                value={gardenOwner}
                onChange={(e) => setGardenOwner(e.target.value)}
                onBlur={() => setIsEditingOwner(false)}
                onKeyPress={(e) => e.key === 'Enter' && setIsEditingOwner(false)}
                placeholder="Your name"
                autoFocus
                className="text-4xl font-bold text-green-900 text-center border-b-2 border-green-500 bg-transparent focus:outline-none"
              />
            </div>
          ) : (
            <h1 
              className="text-4xl font-bold text-green-900 mb-2 cursor-pointer hover:text-green-700 transition inline-flex items-center gap-2"
              onClick={() => setIsEditingOwner(true)}
            >
              {gardenOwner ? `${gardenOwner}'s Garden` : "My Garden"} 
              <Edit2 size={24} className="text-green-600" />
            </h1>
          )}
          <p className="text-green-700">Water plants & air plants - with real care schedules</p>
          <button
            onClick={() => setShowPlantGuide(true)}
            className="mt-2 text-sm text-green-600 hover:text-green-800 underline"
          >
            New to water/air plants? Learn more
          </button>
        </div>

        {/* Birthday Alerts */}
        {upcomingBirthdays.length > 0 && showBirthdayAlert && (
          <div className="bg-yellow-50 border-2 border-yellow-300 rounded-lg p-4 mb-6 relative">
            <button
              onClick={() => setShowBirthdayAlert(false)}
              className="absolute top-2 right-2 text-yellow-600 hover:text-yellow-800"
            >
              <X size={20} />
            </button>
            <div className="flex items-start gap-3">
              <Cake size={24} className="text-yellow-600 mt-1" />
              <div>
                <h3 className="font-semibold text-yellow-900 mb-2">Upcoming Birthdays! 🎉</h3>
                {upcomingBirthdays.map(plant => {
                  const born = new Date(plant.bornDate);
                  const today = new Date();
                  const thisYearBirthday = new Date(today.getFullYear(), born.getMonth(), born.getDate());
                  const daysUntil = Math.ceil((thisYearBirthday - today) / (1000 * 60 * 60 * 24));
                  return (
                    <p key={plant.id} className="text-yellow-800 text-sm">
                      <span className="font-medium">{plant.name}</span> - {daysUntil === 0 ? 'Today!' : `in ${daysUntil} day${daysUntil !== 1 ? 's' : ''}`}
                    </p>
                  );
                })}
              </div>
            </div>
          </div>
        )}

        <div className="bg-white rounded-lg shadow-lg p-6 mb-6">
          <h2 className="text-xl font-semibold text-green-900 mb-4">Add a New Plant</h2>
          <div className="grid grid-cols-1 md:grid-cols-5 gap-4">
            <div className="relative">
              <input
                type="text"
                placeholder="Plant name"
                value={plantName}
                onChange={(e) => setPlantName(e.target.value)}
                className="w-full border border-green-300 rounded px-3 py-2 focus:outline-none focus:ring-2 focus:ring-green-500"
              />
              <button
                onClick={() => setPlantName(generateRandomName())}
                className="absolute right-2 top-1/2 -translate-y-1/2 text-xs text-green-600 hover:text-green-800 font-medium"
              >
                ✨ Random
              </button>
            </div>
            <select
              value={plantType}
              onChange={(e) => setPlantType(e.target.value)}
              className="border border-green-300 rounded px-3 py-2 focus:outline-none focus:ring-2 focus:ring-green-500"
            >
              <optgroup label="Water-Grown Plants">
                <option value="pothos-water">Pothos (Water)</option>
                <option value="lucky-bamboo">Lucky Bamboo</option>
                <option value="spider-plant-water">Spider Plant</option>
                <option value="philodendron-water">Philodendron</option>
                <option value="coleus-water">Coleus</option>
                <option value="mint-water">Mint</option>
                <option value="basil-water">Basil</option>
                <option value="sweet-potato-vine">Sweet Potato Vine</option>
                <option value="english-ivy-water">English Ivy</option>
                <option value="begonia-water">Begonia</option>
              </optgroup>
              <optgroup label="Air Plants">
                <option value="tillandsia-ionantha">Tillandsia Ionantha</option>
                <option value="tillandsia-xerographica">Tillandsia Xerographica</option>
                <option value="spanish-moss">Spanish Moss</option>
                <option value="tillandsia-bulbosa">Tillandsia Bulbosa</option>
                <option value="tillandsia-caput-medusae">Tillandsia Caput-Medusae</option>
                <option value="tillandsia-streptophylla">Tillandsia Streptophylla</option>
                <option value="tillandsia-stricta">Tillandsia Stricta</option>
                <option value="tillandsia-tectorum">Tillandsia Tectorum</option>
                <option value="tillandsia-usneoides">Tillandsia Usneoides</option>
                <option value="tillandsia-brachycaulos">Tillandsia Brachycaulos</option>
              </optgroup>
            </select>
            <div>
              <label className="block text-xs text-gray-600 mb-1">When did you get it? <span className="text-gray-400">(Optional - can approximate or skip)</span></label>
              <input
                type="date"
                value={bornDate}
                onChange={(e) => setBornDate(e.target.value)}
                max={today}
                placeholder="10/dd/2025"
                className="w-full border border-green-300 rounded px-3 py-2 focus:outline-none focus:ring-2 focus:ring-green-500"
              />
            </div>
            <div>
              <label className="block text-xs text-gray-600 mb-1">Last watered/misted</label>
              <input
                type="date"
                value={lastCared}
                onChange={(e) => setLastCared(e.target.value)}
                max={today}
                className="w-full border border-green-300 rounded px-3 py-2 focus:outline-none focus:ring-2 focus:ring-green-500"
              />
            </div>
            <button
              onClick={addPlant}
              className="bg-green-600 text-white rounded px-4 py-2 hover:bg-green-700 transition self-end"
            >
              Add Plant
            </button>
          </div>
        </div>

        {plants.length > 0 && (
          <div className="bg-white rounded-lg shadow-lg p-4 mb-6">
            <div className="flex items-center justify-between">
              <span className="text-sm font-medium text-gray-700 flex items-center gap-2">
                <ArrowUpDown size={16} />
                Sort by:
              </span>
              <div className="flex gap-2">
                <button
                  onClick={() => setSortBy('urgency')}
                  className={`px-3 py-1 rounded text-sm transition ${
                    sortBy === 'urgency' 
                      ? 'bg-green-600 text-white' 
                      : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                  }`}
                >
                  Most Urgent
                </button>
                <button
                  onClick={() => setSortBy('oldest')}
                  className={`px-3 py-1 rounded text-sm transition ${
                    sortBy === 'oldest' 
                      ? 'bg-green-600 text-white' 
                      : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                  }`}
                >
                  Oldest First
                </button>
                <button
                  onClick={() => setSortBy('newest')}
                  className={`px-3 py-1 rounded text-sm transition ${
                    sortBy === 'newest' 
                      ? 'bg-green-600 text-white' 
                      : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
                  }`}
                >
                  Newest First
                </button>
              </div>
            </div>
          </div>
        )}

        <div className="space-y-4">
          {plants.length === 0 ? (
            <div className="bg-white rounded-lg shadow-lg p-12 text-center text-gray-500">
              <p className="text-lg">No plants yet. Add one to start your guilt-free journey!</p>
            </div>
          ) : (
            getSortedPlants().map(plant => {
              const daysOverdue = plant.daysOverdue;
              const daysSinceCare = plant.daysSinceCare;
              const isWatered = plant.isWatered;
              const guiltStatus = getGuiltLevel(daysOverdue);
              const GuiltIcon = guiltStatus.icon;
              const message = getGuiltMessage(daysOverdue, plant.plantInfo.personality, plant.plantInfo.careAction);
              const CareIcon = plant.plantInfo.careType === 'mist' ? Wind : Droplet;

              return (
                <div 
                  key={plant.id} 
                  className={`bg-white rounded-lg shadow-lg p-6 transition cursor-pointer hover:shadow-xl ${
                    plant.isWatered ? 'opacity-80' : ''
                  }`}
                  onClick={() => setSelectedPlant(plant)}
                >
                  <div className="flex items-start justify-between mb-4">
                    <div className="flex items-center gap-3">
                      <div className="relative group">
                        <span className="text-4xl">{plant.emoji}</span>
                      </div>
                      <div>
                        <h3 className="text-xl font-semibold text-green-900">{plant.name}</h3>
                        <p className="text-sm text-green-600">{plant.plantInfo.name}</p>
                        <p className="text-xs text-gray-500">{plant.plantInfo.description}</p>
                      </div>
                    </div>
                    <div className="flex gap-2" onClick={(e) => e.stopPropagation()}>
                      <button
                        onClick={() => !plant.isWatered && carePlant(plant.id)}
                        disabled={plant.isWatered}
                        className={`px-4 py-2 rounded transition flex items-center gap-2 text-sm ${
                          plant.isWatered
                            ? 'bg-gray-300 text-gray-500 cursor-not-allowed'
                            : 'bg-blue-500 text-white hover:bg-blue-600'
                        }`}
                      >
                        <CareIcon size={16} /> 
                        {plant.isWatered ? 'Watered ✓' : (plant.plantInfo.careType === 'mist' ? 'Mist' : 'Change Water')}
                      </button>
                      <button
                        onClick={() => confirmDelete(plant.id)}
                        className="bg-red-500 text-white px-3 py-2 rounded hover:bg-red-600 transition text-sm"
                      >
                        Remove
                      </button>
                    </div>
                  </div>

                  <div className="mb-4 flex flex-wrap gap-3 items-center">
                    <span className={`inline-flex items-center gap-2 px-3 py-1 rounded-full text-sm font-medium ${guiltStatus.color}`}>
                      <GuiltIcon size={16} />
                      {guiltStatus.level.toUpperCase()}
                    </span>
                    <span className="text-gray-600 text-sm">
                      Last {plant.plantInfo.careAction}: {plant.daysSinceCare} day{plant.daysSinceCare !== 1 ? 's' : ''} ago
                    </span>
                    {plant.daysOverdue > 0 && (
                      <span className="text-red-600 font-semibold text-sm">
                        ({plant.daysOverdue} day{plant.daysOverdue !== 1 ? 's' : ''} overdue!)
                      </span>
                    )}
                    {plant.daysOverdue <= 0 && (
                      <span className="text-green-600 font-semibold text-sm">
                        (Next care in {Math.abs(plant.daysOverdue)} day{Math.abs(plant.daysOverdue) !== 1 ? 's' : ''})
                      </span>
                    )}
                  </div>

                  {!plant.isWatered && (
                    <div className="bg-gray-50 rounded-lg p-4 italic text-gray-700 border-l-4 border-green-500">
                      "{message}"
                    </div>
                  )}
                </div>
              );
            })
          )}
        </div>

        {/* Delete Confirmation Modal */}
        {deleteConfirm && (
          <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
            <div className="bg-white rounded-lg shadow-xl p-6 max-w-md mx-4">
              <h3 className="text-xl font-bold text-gray-900 mb-2">Abandon Plant? 🥺</h3>
              <p className="text-gray-600 mb-6">
                Are you sure you want to remove <span className="font-semibold">{plants.find(p => p.id === deleteConfirm)?.name}</span>? 
                They'll be gone forever (or until you add them back).
              </p>
              <div className="flex gap-3 justify-end">
                <button
                  onClick={cancelDelete}
                  className="px-4 py-2 bg-gray-200 text-gray-800 rounded hover:bg-gray-300 transition"
                >
                  Cancel
                </button>
                <button
                  onClick={() => deletePlant(deleteConfirm)}
                  className="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600 transition"
                >
                  Yes, Remove
                </button>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}
