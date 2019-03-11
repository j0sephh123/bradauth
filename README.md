Test auth

Register user
// @route   POST api/users/register
// @desc    Register user
// @access  Public
http://localhost:5000/api/users/register
{
	"name": "ivan",
	"email": "ivan@abv.bg",
	"password": "asdasd",
	"password2": "asdasd"
}
--------------------------------------------------------
Login
// @route   GET api/users/login
// @desc    Login User / Returning JWT Token
// @access  Public

http://localhost:5000/api/users/login
{
	"email": "ivan@abv.bg",
	"password": "asdasd"
}
--------------------------------------------------------
// @route   GET api/users/current
// @desc    Return current user
// @access  Private
router.get(
  '/current',
  passport.authenticate('jwt', { session: false }),
  (req, res) => {
    res.json({
      id: req.user.id,
      name: req.user.name,
      email: req.user.email
    });
  }
);