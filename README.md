import React, { useState } from 'react';
import './App.css'; // Add your CSS file if needed

const App = () => {
  const [currentHeaderTextIndex, setCurrentHeaderTextIndex] = useState(0);
  const [yesButtonSize, setYesButtonSize] = useState(1);
  const [yesButtonBouncing, setYesButtonBouncing] = useState(false);
  const [noButtonClicked, setNoButtonClicked] = useState(false);

  const headerText = [
    'Do you love me?',
    'Are you in love with me?',
    'Do you love me very much?',
    'Don\'t you love me at all?',
    'Not at all?',
  ];

  const changeText = (button) => {
    if (button === 'noButton') {
      setCurrentHeaderTextIndex((currentHeaderTextIndex + 1) % headerText.length);
      setYesButtonSize(yesButtonSize + 5);
      setYesButtonBouncing(true);
      setTimeout(() => {
        setYesButtonBouncing(false);
      }, 500);

      // Trigger crying animation
      setNoButtonClicked(true);
      setTimeout(() => {
        setNoButtonClicked(false);
      }, 500);
    }
  };

  const yesButton = () => {
    alert('I love you too');
  };

  const currentHeaderText = headerText[currentHeaderTextIndex];

  return (
    <div className="love-container">
      {/* Love Meter Section */}
      <div id="love-meter" className="love-meter">
        <h3 onClick={() => changeText('heading')}>{currentHeaderText}</h3>
        <button
          type="button"
          className={`btn btn-success btn-yes ${yesButtonBouncing ? 'bounce' : ''}`}
          style={{ fontSize: `${yesButtonSize}rem` }}
          onClick={yesButton}
        >
          Yes
        </button>
        <button
          type="button"
          className={`btn btn-danger btn-no ${noButtonClicked ? 'cry-animation' : ''}`}
          onClick={() => changeText('noButton')}
        >
          No, I don't love
        </button>
      </div>

      {/* Love Gif Section */}
      <div className="love-gif">
        <a
          className="mfp-img-link"
          href="https://www.gifcen.com/wp-content/uploads/2021/02/love-gif.gif"
          title="Love Gif"
        >
          <img
            className="mfp-img"
            alt="Love Gif"
            src="https://www.gifcen.com/wp-content/uploads/2021/02/love-gif.gif"
            style={{ maxHeight: '400px' }}
          />
        </a>
      </div>
    </div>
  );
};

export default App;
